<script>
	import { navigate } from "svelte-routing";

    let questionCount = 1
  </script>
  
  <main class="w-screen h-screen flex flex-col items-center justify-center" >
    <div class="flex gap-5">
  
      <input type="text" bind:value={questionCount} placeholder="Number of Questions" class="input input-bordered w-full max-w-xs rounded-full" />
      
      <button class="btn" on:click={() => {
        navigate('/question-paper/'+questionCount)
      }} >Generate</button>
      </div>
  </main>