<script lang="ts">
    // Ejemplo de categorías y precios para filtrar
    let categories = ["Electrónica", "Ropa", "Accesorios", "Hogar"];
    let priceRanges = [
      { label: "Bajo $50", value: "0-50" },
      { label: "$50 - $100", value: "50-100" },
      { label: "$100 - $500", value: "100-500" },
      { label: "Más de $500", value: "500-1000" },
    ];
  
    // 50 productos con imágenes de ejemplo
    let products = Array(50).fill(null).map((_, index) => ({
      name: `Producto ${index + 1}`,
      category: ["Electrónica", "Ropa", "Accesorios", "Hogar"][index % 4],
      price: (Math.random() * 500).toFixed(2),
      rating: Math.ceil(Math.random() * 5),
      description: `Descripción del Producto ${index + 1}`,
      imageUrl: `https://via.placeholder.com/300x200?text=Producto+${index + 1}`,
    }));
  
    // Filtros
    let selectedCategory = "";
    let selectedPriceRange = "";
    let filteredProducts = products;
  
    const filterProducts = () => {
      filteredProducts = products.filter((product) => {
        const matchesCategory = selectedCategory ? product.category === selectedCategory : true;
        const matchesPrice = selectedPriceRange
          ? product.price >= parseInt(selectedPriceRange.split("-")[0]) &&
            product.price <= parseInt(selectedPriceRange.split("-")[1])
          : true;
        return matchesCategory && matchesPrice;
      });
    };
  
    // Carrito de compras
    let cart: any[] = [];
  
    // Función para agregar productos al carrito
    const addToCart = (product: any) => {
      cart = [...cart, product];
      alert(`${product.name} ha sido agregado al carrito`);
    };
  </script>
  
  <div class="flex">
    <!-- Barra lateral fija con fondo morado difuso y menor anchura -->
    <div class="w-1/5 bg-gradient-to-b from-purple-400 via-purple-300 to-purple-200 p-6 rounded-md sticky top-0 shadow-lg">
      <h2 class="text-lg font-bold mb-4 text-white">Filtros</h2>
  
      <!-- Filtro por categoría -->
      <div class="mb-4">
        <h3 class="font-semibold text-white">Categoría</h3>
        <select bind:value={selectedCategory} on:change={filterProducts} class="w-full p-2 border rounded-md">
          <option value="">Todas</option>
          {#each categories as category}
            <option value={category}>{category}</option>
          {/each}
        </select>
      </div>
  
      <!-- Filtro por rango de precio -->
      <div class="mb-4">
        <h3 class="font-semibold text-white">Precio</h3>
        <select bind:value={selectedPriceRange} on:change={filterProducts} class="w-full p-2 border rounded-md">
          <option value="">Todos</option>
          {#each priceRanges as range}
            <option value={range.value}>{range.label}</option>
          {/each}
        </select>
      </div>
    </div>
  
    <!-- Productos -->
    <div class="flex-1">
      <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6 p-4">
        {#each filteredProducts as product}
          <div class="bg-white p-4 rounded-md shadow-md hover:shadow-xl transition-all duration-200 transform hover:scale-105">
            <!-- Imagen del producto con efecto de aumento -->
            <div class="relative">
              <img src={product.imageUrl} alt={product.name} class="w-full h-48 object-cover rounded-md transition-transform duration-300 transform hover:scale-110" />
              <div class="absolute top-0 left-0 w-full h-full bg-black bg-opacity-25 rounded-md transition-all duration-300 transform opacity-0 hover:opacity-100"></div>
            </div>
            <h3 class="font-semibold text-lg mt-4">{product.name}</h3>
            <p class="text-sm text-gray-600">Categoría: {product.category}</p>
            <p class="text-sm text-gray-600">Precio: ${product.price}</p>
            <p class="text-sm text-gray-600">Calificación: {product.rating} ⭐</p>
            <p class="text-xs text-gray-500">{product.description}</p>
  
            <!-- Botón para agregar al carrito -->
            <button on:click={() => addToCart(product)} class="mt-4 w-full bg-purple-600 text-white py-2 rounded-md hover:bg-purple-700 focus:outline-none focus:ring-2 focus:ring-purple-500 focus:ring-opacity-50">
              Agregar al carrito
            </button>
          </div>
        {/each}
      </div>
    </div>
  </div>
  
  <style>
    /* Efecto de imagen en hover */
    .hover\:scale-110:hover {
      transform: scale(1.1);
    }
  
    /* Efecto de aumento de imagen */
    .transition-transform {
      transition: transform 0.3s ease-in-out;
    }
  
    /* Barra lateral con difuminado morado */
    .bg-gradient-to-b {
      background: linear-gradient(to bottom, rgba(147, 112, 219, 1) 0%, rgba(230, 184, 255, 1) 100%);
    }
  </style>
  