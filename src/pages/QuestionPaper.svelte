<script>
	import _ from "underscore";
	import { navigate } from "svelte-routing";

	export let questionCount;
	let questionRange = _.range(1, parseInt(questionCount) + 1);
	let selectedAnswers = new Array(questionRange.length).fill(null);

	const handleCheck = () => {
        navigate('/summary', {state: {selectedAnswers}})
    };

	const handleKeyPress = (event, index) => {
		const key = event.key;
		const options = ["A", "B", "C", "D"];
		const optionIndex = parseInt(key) - 1;

		if (optionIndex >= 0 && optionIndex < options.length) {
			selectedAnswers[index] = options[optionIndex];

			// Find the next question input element
			const nextInput = document.querySelector(`[name="question-${index + 1}"][value="${options[0]}"]`);
			if (nextInput) {
				nextInput.focus();
			}
		}
	};
</script>

<main class="flex flex-col">
	<div class="grid grid-cols-2 space-y-2 p-5 gap-5">
		{#each questionRange as number, index}
			<div class="card w-full bg-base-100 shadow-xl">
				<div class="card-body">
					<h2 class="card-title">{`Question ${number}`}</h2>
					<div class="card-actions justify-end"></div>
					<div class="form-control" on:keydown={(event) => handleKeyPress(event, index)} tabindex="0">
						<label class="label cursor-pointer">
							<span class="label-text">A</span>
							<input
								type="radio"
								name={`question-${index}`}
								value="A"
								class="radio checked:bg-red-500"
								bind:group={selectedAnswers[index]}
							/>
						</label>
						<label class="label cursor-pointer">
							<span class="label-text">B</span>
							<input
								type="radio"
								name={`question-${index}`}
								value="B"
								class="radio checked:bg-red-500"
								bind:group={selectedAnswers[index]}
							/>
						</label>
						<label class="label cursor-pointer">
							<span class="label-text">C</span>
							<input
								type="radio"
								name={`question-${index}`}
								value="C"
								class="radio checked:bg-red-500"
								bind:group={selectedAnswers[index]}
							/>
						</label>
						<label class="label cursor-pointer">
							<span class="label-text">D</span>
							<input
								type="radio"
								name={`question-${index}`}
								value="D"
								class="radio checked:bg-red-500"
								bind:group={selectedAnswers[index]}
							/>
						</label>
					</div>
				</div>
			</div>
		{/each}
	</div>
	<button class="btn btn-primary self-center" on:click={handleCheck}>Check</button>
</main>

<style>
	/* Add some styling to ensure the focus is visible */
	:focus {
		outline: 2px solid blue;
	}
</style>
