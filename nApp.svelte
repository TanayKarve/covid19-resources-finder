<head>
	<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
</head>
<script>
  import City from "./City.svelte";

  import { getCity } from "./City.svelte";
  import { requirementStore } from "./store.js";
  import Requirements from "./Requirements.svelte";
  import { getRequirements } from "./Requirements.svelte";

  import { Jumbotron, Button, Card, CustomInput, Badge } from "sveltestrap";
  var verified = true;
  function toggleVerification() {
    verified = !verified;
  }
  var query = "";
  const src =
    "https://img.republicworld.com/republic-prod/stories/images/15961176185f22d272e6a8f.png";
  function generateQuery() {
    var city = getCity();
    if (city == "") {
	    alert("Please enter city name!");
	    return;
    }
    var requirements = getRequirements();
    //var ret = $requirementStore; //.getItem("requirements");
    query = "http://twitter.com/search?q=";
    if (verified) query += "verified ";
    //console.log(requirements);
    requirements = requirements.replace(/\s+/g, ",");
    requirements = requirements.split(",");
    //console.log(requirements);
    requirements = requirements.join(" OR ");
    //console.log(requirements);

    //requirements = requirements.replaceAll(" ", " OR ");
    var filters =
      ' -"not verified" -"unverified" -"needed" -"need" -"needs" -"required" -"require" -"requires" -"requirement" -"requirements"';
    query += city + " (" + requirements + ")" + filters + "&f=live";
    query = encodeURI(query);
    //console.log(query);
    window.open(query, "_blank");
  }
</script>

<style>
  * {
    font-family: fa5-proxima-nova, "Helvetica Neue", Helvetica, Arial, sans-serif;
  }
  div {
    margin: 4%;
  }

  .center {
    position: relative;
    text-align: center;
    font-weight: bold;
  }
</style>
<!-- <Style/> -->
<body>




<br>
  
<Jumbotron>
<div>

  <City/>
  </div>
  <div>
  <Requirements/>
  </div>

  <div class="center" >

  <Card>
<div style="margin:4%">

  <CustomInput
        type="switch"
        checked
        
        on:change={toggleVerification}
        id="exampleCustomSwitch"
        name="customSwitch"
        label={verified ? "VERIFIED ONLY" : "UNVERIFIED"} />
</div>
  </Card>
  </div>

  <div class="center">
<Button on:click={generateQuery} block color='danger' >SEARCH</Button>
    <!-- <Button color='success' block> -->
  
  <!-- <a href={query} target="_blank" rel="noopener noreferrer">SEARCH</a> -->
    <!-- </Button> -->
  </div>
  
</Jumbotron>

</body>
<footer >

  <!-- Copyright -->
  <div class="footer-copyright text-center py-3">
    <a href="https://github.com/TanayKarve/covid19-resources-finder">Project Homepage and Source Code</a>
  </div>
  <!-- Copyright -->

</footer>

