<script>
	import Header from '$lib/header/Header.svelte';
	import '../app.css';
	// import { afterUpdate } from 'svelte';
	let JsonObject = '';

	let isJsonObjectValid = false;
	const handleJsonChange = (e) => {
		JsonObject = e.target.value;
		let temp = [];
		for (let i = 0; i < JsonObject.length; i++) {
			if (JsonObject[i] === '[' || JsonObject[i] === ']') {
				console.log('first');
				temp.push('');
			} else {
				temp.push(JsonObject[i]);
			}
		}
		let dummyJSON = JSON.stringify(temp);
    // console.log("@jawad ~ file: __layout.svelte ~ line 21 ~ dummyJSON", dummyJSON)
		let JSONStringObject = JSON.parse(dummyJSON);
    console.log("@jawad ~ file: __layout.svelte ~ line 22 ~ JSONStringObject", JSONStringObject)
		try {
			let JSONString = JSON.parse(JsonObject);
			if (
				JSONString.check?.charAt(0) != '[' ||
				JSONString.check.charAt(JSONString.check.length - 1) != ']'
			) {
				isJsonObjectValid = true;
				console.log(isJsonObjectValid);
			} else if (
				JSONString.check?.charAt(0) === '[' &&
				JSONString.check.charAt(JSONString.check.length - 1) === ']'
			) {
				// console.log(JSONString.check?.charAt(0));
				JSONString.shift();
				JSONString.pop();
				isJsonObjectValid = true;
				console.log(isJsonObjectValid);
			}
			return true;
		} catch (e) {
			isJsonObjectValid = false;
			console.log(e);
			console.log(isJsonObjectValid);
			return false;
		}
	};
</script>

<Header />
<main>
	<section>
		<div class="flex justify-center items-center">
			<div class="grid grid-cols-2 mx-auto  w-11/12 gap-x-3 ">
				<form on:submit class="w-full text-gray-700 pb-2 ">
					<textarea
						class="text-gray-500 text-sm w-full placeholder:py-2 border-2 rounded-lg placeholder:px-3 py-2 placeholder:text-xs outline-none h-full"
						placeholder="Paste your JSON code here"
						on:input={handleJsonChange}
						bind:value={JsonObject}
						on:input={handleJsonChange}
					/>
				</form>
				<div class="px-20 py-2 text-gray-700 border-2 rounded-lg bg-cyan-800 mb-2">
					<div class="flex flex-col justify-center gap-y-2 py-6">
						<div
							class="flex border-yellow-500 px-2 py-2 border-2 text-md rounded-md text-yellow-500 transform hover:scale-105 bg-white  transition duration-500 cursor-pointer"
						>
							<div class="px-2">
								<svg
									xmlns="http://www.w3.org/2000/svg"
									class="h-4  w-4 fill-white "
									fill="currentColor"
									viewBox="0 0 24 24"
									stroke="currentColor"
									stroke-width="2"
								>
									<path
										stroke-linecap="round"
										stroke-linejoin="round"
										d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z"
									/>
								</svg>
							</div>
							<h6 class="text-xs">Basic JSON validation</h6>
							<!-- {console.log({ asdad: isJsonObjectValid })} -->
							<p class="pl-4 text-xs">{isJsonObjectValid}</p>
						</div>
						<div
							class="flex border-red-500 px-2 py-2 border-2 text-md rounded-md text-red-500 transform hover:scale-105 bg-white  transition duration-500 cursor-pointer"
						>
							<div class="px-2">
								<svg
									xmlns="http://www.w3.org/2000/svg"
									class="h-4  w-4 fill-white "
									fill="currentColor"
									viewBox="0 0 24 24"
									stroke="currentColor"
									stroke-width="2"
								>
									<path
										stroke-linecap="round"
										stroke-linejoin="round"
										d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z"
									/>
								</svg>
							</div>
							<h6 class="text-xs">Removed squared brackets</h6>
							<!-- {console.log({ asdad: isJsonObjectValid })} -->
							<!-- <p class="pl-4 text-xs">{isJsonObjectValid}</p> -->
						</div>
						<img
							src="https://media.giphy.com/media/3oEjI9xj49ehuAGLQY/giphy.gif"
							class="rounded-md"
							alt="code"
						/>
					</div>
				</div>
			</div>
		</div>
	</section>
</main>
<footer class="bottom-0 absolute mx-auto right-0 left-0">
	<p>
		<a
			class="text-xs font-mono text-gray-500 no-underline hover:no-underline transition duration-300 hover:opacity-60 transform hover:scale-125"
			target="_blank"
			href="https://www.linkedin.com/in/jawad-basit/">Developed by Jawad Ahmed</a
		>
	</p>
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
	@media (min-width: 480px) {
		footer {
			padding: 40px 0;
		}
	}
</style>
