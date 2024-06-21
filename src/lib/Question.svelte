<script>
  export let text
  import Options from "./Options.svelte";
</script>

<div class="card w-full bg-base-100 shadow-xl">
  <div class="card-body">
    <h2 class="card-title">{text}</h2>
    <div class="card-actions justify-end">
    </div>
    <Options/>
  </div>
</div>