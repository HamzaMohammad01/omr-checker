<script>
    export let ques
    export let exp
    export let border
</script>

<div class="collapse collapse-arrow bg-base-200 border-2 {border}">
  <input type="radio" name="my-accordion-2" /> 
  <div class="collapse-title text-xl font-medium">
    {ques}
  </div>
  <div class="collapse-content"> 
    {@html exp}
  </div>
</div>