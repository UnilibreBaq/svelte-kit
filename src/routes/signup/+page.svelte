<script>
    import { onMount } from 'svelte';
    let name = "";
    let email = "";
    let password = "";
    let confirmPassword = "";
    let error = "";
    let successMessage = "";
  
    const handleSubmit = (event) => {
      event.preventDefault();
  
      // Validación básica
      if (name === "" || email === "" || password === "" || confirmPassword === "") {
        error = "Por favor, complete todos los campos";
        return;
      }
  
      if (password !== confirmPassword) {
        error = "Las contraseñas no coinciden";
        return;
      }
  
      // Si pasa la validación, puedes continuar con la lógica de registro (guardar en base de datos, etc.)
      successMessage = "¡Te has registrado exitosamente! Ahora puedes iniciar sesión.";
      error = "";
  
      // Aquí iría la lógica para registrar al usuario (por ejemplo, hacer un fetch a una API).
      console.log("Registrando:", { name, email, password });
    };
  </script>
  
  <main class="flex items-center justify-center h-screen bg-purple-100">
    <div class="w-full max-w-md p-8 space-y-4 bg-white rounded-lg shadow-md">
      <h2 class="text-2xl font-bold text-center text-purple-600">Registrarse</h2>
  
      {#if error}
        <div class="text-red-500 text-center">{error}</div>
      {/if}
  
      {#if successMessage}
        <div class="text-green-500 text-center">{successMessage}</div>
      {/if}
  
      <form on:submit={handleSubmit} class="space-y-4">
        <!-- Campo de Nombre -->
        <div>
          <label for="name" class="block text-sm font-medium text-gray-700">Nombre completo</label>
          <input
            type="text"
            id="name"
            bind:value={name}
            required
            class="mt-1 block w-full p-2 border border-gray-300 rounded-md focus:ring-2 focus:ring-purple-500 focus:outline-none"
            placeholder="Juan Pérez"
          />
        </div>
  
        <!-- Campo de Correo electrónico -->
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
  
        <!-- Campo de Contraseña -->
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
  
        <!-- Campo de Confirmación de Contraseña -->
        <div>
          <label for="confirmPassword" class="block text-sm font-medium text-gray-700">Confirmar contraseña</label>
          <input
            type="password"
            id="confirmPassword"
            bind:value={confirmPassword}
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
            Registrarse
          </button>
        </div>
  
        <div class="text-center">
          <p class="text-sm text-gray-600">
            ¿Ya tienes cuenta? <a href="/login" class="text-purple-600 hover:underline">Inicia sesión</a>
          </p>
        </div>
      </form>
    </div>
  </main>