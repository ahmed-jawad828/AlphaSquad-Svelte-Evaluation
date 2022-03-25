<script>
	import Header from '$lib/header/Header.svelte';
	import '../app.css';
	import { afterUpdate } from 'svelte';
	let JsonObject = 'asdas';

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
		// JsonObject = temp;
		try {
			let JSONString = JSON.parse(JsonObject);
			// console.log(
			// 	'🚀 ~ file: __layout.svelte ~ line 12 ~ handleJsonChange ~ JSONString',
			// 	JSONString
			// );
			JSONString.check?.charAt(0)

			// console.log(
			// console.lo({arif nhattrri})
)
			if (
				JSONString.check?.charAt(0) != '[' ||
				JSONString.check.charAt(JSONString.check.length - 1) != ']'
			) {
				console.log('first');
				isJsonObjectValid = true;
				console.log(isJsonObjectValid);
			}

			if (
				JSONString.check?.charAt(0) === '[' &&
				JSONString.check?.charAt(JSONString.check.length - 1) === ']'
			) {
				console.log('Second');
				JSONString.shift();
				JSONString.pop();
				console.log(
					'🚀 ~ file: __layout.svelte ~ line 23 ~ handleJsonChange ~ JSONString',
					JSONString
				);
				isJsonObjectValid = true;
				console.log(isJsonObjectValid);
			}
			if (JSONString.check?.charAt(0) === '[') {
				JSONString.shift();

				console.log(
					'🚀 ~ file: __layout.svelte ~ line 23 ~ handleJsonChange first ~ JSONString',
					JSONString
				);
				isJsonObjectValid = true;
				console.log(isJsonObjectValid);
			}
			if (JSONString.check.charAt(JSONString.check.length - 1) != ']') {
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
	console.log('🚀 ~ file: __layout.svelte ~ line 6 ~ JsonObject', JsonObject);
</script>

<Header />
<main>
	<section>
		<div class="flex justify-center items-center">
			<div class="grid grid-cols-2 mx-auto  w-10/12 ">
				<form on:submit class="w-full text-gray-700 border-2 rounded-lg">
					<textarea
						class="text-gray-500 text-sm w-full placeholder:py-2 placeholder:px-3 py-2 placeholder:text-xs outline-none"
						rows="6"
						placeholder="Paste your JSON code here"
						on:input={handleJsonChange}
						bind:value={JsonObject}
						on:input={handleJsonChange}
					/>
				</form>
				<div class="px-3 py-2 text-gray-700 border-2 rounded-lg bg-white mb-2">
					<div class="flex flex-col justify-center">
						<div class="flex">
							<h6 class="text-xs">Basic JSON validation</h6>
							<!-- {console.log({ asdad: isJsonObjectValid })} -->
							<p class="pl-4 text-xs">{isJsonObjectValid}</p>
						</div>
						<div>
							<h6 class="text-xs">Removed squared brackets</h6>
						</div>
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
