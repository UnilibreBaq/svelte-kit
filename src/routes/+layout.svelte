<script lang="ts">
	import '../app.css';
	let { children } = $props();
</script>

<div class="app">
	 <!-- Encabezado -->
	 <header class="bg-purple-700 text-white py-4">
		<div class="max-w-7xl mx-auto px-4 flex justify-between items-center">
		  <h1 class="text-3xl font-semibold">UPANA</h1>
		  <nav>
			<a href="login" class="text-lg hover:text-purple-300">Iniciar sesión</a>
		  </nav>
		</div>
	  </header>
	
	 
	{@render children()}
</div>


