<script>
    let email = "";
    let password = "";
    let error = "";
  
  </script>
  
  <main class="flex items-center justify-center h-screen bg-purple-100">
    <div class="w-full max-w-md p-8 space-y-4 bg-white rounded-lg shadow-md">
      <h2 class="text-2xl font-bold text-center text-purple-600">Iniciar sesión</h2>
  
      {#if error}
        <div class="text-red-500 text-center">{error}</div>
      {/if}
  
      <form class="space-y-4">
        <div>
          <label for="email" class="block text-sm font-medium text-gray-700">Correo electrónico</label>
          <input
            type="email"
            id="email"
            bind:value={email}
            required
            class="mt-1 block w-full p-2 border border-gray-300 rounded-md focus:ring-2 focus:ring-purple-500 focus:outline-none"
            placeholder="juan@example.com"
          />
        </div>
  
        <div>
          <label for="password" class="block text-sm font-medium text-gray-700">Contraseña</label>
          <input
            type="password"
            id="password"
            bind:value={password}
            required
            class="mt-1 block w-full p-2 border border-gray-300 rounded-md focus:ring-2 focus:ring-purple-500 focus:outline-none"
            placeholder="********"
          />
        </div>
  
        <div class="flex items-center justify-between">
          <button
            type="submit"
            class="w-full bg-purple-600 text-white py-2 px-4 rounded-md hover:bg-purple-700 focus:outline-none focus:ring-2 focus:ring-purple-500"
          >
            Iniciar sesión
          </button>
        </div>
  
        <div class="text-center">
          <p class="text-sm text-gray-600">
            ¿No tienes cuenta? <a href="/signup" class="text-purple-600 hover:underline">Regístrate</a>
          </p>
        </div>
      </form>
    </div>
  </main>