<script>
	import Header from '$lib/header/Header.svelte';
	import '../app.css';
</script>

<Header />

<main>

  <section>
    <div class="bg-red-700 flex justify-center items-center">
      <div class="grid grid-cols-2 ">
        <div class=''>
          <form on:submit>
            <textarea
            class=" px-3 py-2 text-gray-500 w-[500px] border-2 rounded-lg"
            rows="6"
            placeholder="Paste your JSON code here"            
            />           
          </form>
        </div>
        <div class='px-3 py-2 text-gray-700 border-2 w-[500px] rounded-lg'>asdasdadasdasdasdas</div>
      </div>
    </div>
  </section>
	<!-- <slot /> -->
</main>

<footer>
	<!-- <p>visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to learn SvelteKit</p> -->
</footer>

<style>
	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 1024px;
		margin: 0 auto;
		box-sizing: border-box;
	}
	footer {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding: 40px;
	}

	footer a {
		font-weight: bold;
	}

	@media (min-width: 480px) {
		footer {
			padding: 40px 0;
		}
	}
</style>
