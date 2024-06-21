<script>
	import correctAnswers from "../utils/correctAnswers";
  export let selectedAnswers
  let wrongAnswers = 0
  for (let i = 0; i < selectedAnswers.length; i++) {
    console.log(selectedAnswers[i])
    // console.log(wrongAnswers[i])
    // if(selectedAnswers[i] !== correctAnswers[i].ans.toLowerCase()) {
    //   wrongAnswers += 1;
    // }
  }

</script>

<dialog id="my_modal_3" class="modal">
  <div class="modal-box">
    <form method="dialog">
      <button class="btn btn-sm btn-circle btn-ghost absolute right-2 top-2">✕</button>
    </form>
    <h1>Summary</h1>
    <p>You got {wrongAnswers} wrong answers</p>
  </div>
</dialog>