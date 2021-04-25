<style>
  h2,
  h1,
  .leads {
    margin: 4%;
  }
  .warning {
    font-weight: bold;
    color: red;
  }
</style>
<script context="module">
  import { cities } from "./cities";
  import Select from "svelte-select";
  import { Button } from "sveltestrap";
  import Content from "./Content.svelte";
  import Modal from "svelte-simple-modal";
  import { Card } from "sveltestrap";
  import { getContext } from "svelte";
  import Warning from "./Warning.svelte";

  var city = "";
  function handleSelectCity(event) {
    city = event.detail.value;

    //console.log(city);
  }
  export function getCity() {
    return city;
  }
</script>

<Card>
<div style="margin:4%">
<h1 >Covid Digital Helper</h1>

	<div class="leads">
		This is a simple tool to help you search for valuable covid-19 resources online.
  <br><a href="https://www.instagram.com/reel/COFOFu6J7tY/">Tutorial</a>
<div class='warning'>
		Do NOT make advanced payments unless you are 100% sure about their authenticity.
		<br>Check for replies under the tweets.
</div>
</div>
 

<h2>City</h2>
<Select id="cities" placeholder="Enter city name here" items={cities} on:select={handleSelectCity}></Select>
<div>
</Card>
