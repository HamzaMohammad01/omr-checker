<script>
  import { Router, Link, Route } from "svelte-routing";
  import Home from './pages/Home.svelte'
	import QuestionPaper from "./pages/QuestionPaper.svelte";
	import Summary from "./pages/Summary.svelte";
  export let url = "";
</script>

<Router {url}>
  <div>
    <Route path="/"><Home /></Route>
    <Route path="question-paper/:questionCount" let:params>
      <QuestionPaper questionCount={params.questionCount} />
    </Route>
    <Route path='summary'>
      <Summary/>
    </Route>
  </div>
</Router>