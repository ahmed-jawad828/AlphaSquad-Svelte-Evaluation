<script>
	import Header from '$lib/header/Header.svelte';
	import '../app.css';
	let JsonObject = '';
	let isJsonObjectValid = false;
	const handleJsonChange = (e) => {
		// console.log('🚀 ~ file: __layout.svelte ~ line 31 ~ handleJsonChange ~ e', e.target.value);
		JsonObject = e.target.value;
		// console.log('🚀 ~ file: __layout.svelte ~ line 9 ~ handleJsonChange ~ JsonObject', JsonObject);
		let newString = JsonObject.replace('[', '');
		// newStr = str.replace('[', '');
		console.log('🚀 ~ file: __layout.svelte ~ line 10 ~ handleJsonChange ~ newString', newString);
		// console.log(
		// 	'🚀 ~ file: __layout.svelte ~ line 9 ~ handleJsonChange ~ JsonObject',
		// 	JsonObject[30]
		//  );
		// JsonObject = newString;
		// let str = 'AppDividend';
		console.log('Original String: ', JsonObject);

		// let newStr = JsonObject.replace(/D/g, '');
		// console.log('After character removed: ', newStr);
		try {
			let JSONString = JSON.parse(JsonObject);
			// console.log(
			// 	'🚀 ~ file: __layout.svelte ~ line 12 ~ handleJsonChange ~ JSONString',
			// 	JSONString
			// );
			// console.log(
			// 	'🚀 ~ file: __layout.svelte ~ line 18 ~ handleJsonChange ~ JSONString.check?.charAt(0)',
			// 	JSONString.check?.charAt(0)
			// );
			if (
				JSONString.check?.charAt(0) != '[' ||
				JSONString.check.charAt(JSONString.check.length - 1) != ']'
			) {
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
			<div class="grid grid-cols-2 mx-auto  w-10/12 ">
				<form on:submit class="w-full text-gray-700 border-2 rounded-lg">
					<textarea
						class="text-gray-500 text-sm w-full placeholder:py-2 placeholder:px-3 py-2 placeholder:text-xs outline-none"
						rows="6"
						placeholder="Paste your JSON code here"
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
