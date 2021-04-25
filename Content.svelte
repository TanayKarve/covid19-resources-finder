<script>
  import { getContext } from "svelte";
  import Warning from "./Warning.svelte";

  const { open } = getContext("simple-modal");

  const showSurprise = () => {
    open(Warning, { message: "Important!" });
  };
</script>


<p><button on:click={showSurprise}>Show me a surprise!</button></p>