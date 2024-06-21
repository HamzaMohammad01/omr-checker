<script>
	import { onMount } from "svelte";
	import correctAnswers from "../utils/correctAnswers";
    import Accordion from "../lib/Accordian.svelte";
	import Accordian from "../lib/Accordian.svelte";

	let selectedAnswers = [];
	let wrongAnswers = [];
	let nonAttempted = [];
	let correctAnswersCount = 0;
    let negativeMarking = 1/3

	onMount(() => {
		selectedAnswers = history.state.selectedAnswers || [];
        console.log(selectedAnswers)
		
		selectedAnswers.forEach((answer, index) => {
			if (answer === null) {
				nonAttempted.push(index);
                nonAttempted = nonAttempted
			} else if (answer.toLowerCase() !== correctAnswers[index].ans.toLowerCase()) {
				wrongAnswers.push(index);
                wrongAnswers = wrongAnswers
			} else {
				correctAnswersCount++;
			}
		});
	});
</script>

<main class="flex flex-col items-center gap-5 p-5 bg-slate-100 h-screen">
    <div class="flex gap-5 justify-center">

        <div class="flex flex-col justify-center items-center w-fit">
            <div class="radial-progress text-primary" style="--value:{correctAnswersCount/selectedAnswers.length*100};" role="progressbar">{correctAnswersCount}</div>
            Correct Answers
        </div>
        <div class="flex flex-col justify-center items-center w-fit">
            <div class="radial-progress text-primary" style="--value:{nonAttempted.length/selectedAnswers.length*100};" role="progressbar">{nonAttempted.length}</div>
            Not Attempted
        </div>
        <div class="flex flex-col justify-center items-center w-fit">
            <div class="radial-progress text-primary" style="--value:{wrongAnswers.length/selectedAnswers.length*100};" role="progressbar">{wrongAnswers.length}</div>
            Wrong Answers
        </div>
        <div class="stats shadow">
            <div class="stat">
                <div class="stat-title">Total Score</div>
                <div class="stat-value">{((correctAnswersCount*2)-(wrongAnswers.length*2*negativeMarking)).toFixed(2)}</div>
            </div>
        </div>
    </div>

          <div class="flex flex-col gap-5">
              {#each selectedAnswers as selected,i} 
              <Accordian ques={`Question ${i+1}`} exp={correctAnswers[i].exp} border={wrongAnswers.includes(i)?'border-red-500':nonAttempted.includes(i)?'border-yellow-500':'border-primary'} />
              {/each}
            </div>
          
</main>

<style>
	h1, h2 {
		margin-bottom: 1rem;
	}
	p {
		margin-bottom: 0.5rem;
	}
	ul {
		list-style-type: disc;
		padding-left: 2rem;
	}
</style>
