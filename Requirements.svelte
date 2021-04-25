<style>
  h2 {
    margin: 4%;
  }
</style>
<script context="module" >
  const alsoSearchFor = {
    Beds: {
      keywords: ["bed", "beds"],
      checked: true,
      icon: ["fas", "bed"]
    },
    ICU: {
      keywords: ["icu"],
      checked: true,
      icon: ["fas", "procedures"]
    },
    Oxygen: {
      keywords: ["oxygen"],
      checked: true,
      icon: ["fas", "lungs"]
    },
    Ventilator: {
      keywords: ["ventilator", "ventilators"],
      checked: true,
      icon: ["fas", "heartbeat"]
    },
    Tests: {
      keywords: ["test", "tests", "testing"],
      checked: false,
      icon: ["fas", "vial"]
    },
    Fabiflu: {
      keywords: ["fabiflu"],
      checked: false,
      icon: ["fas", "pills"]
    },
    Remdesivir: {
      keywords: ["remdesivir"],
      checked: false,
      icon: ["fas", "tablets"]
    },
    Favipiravir: {
      keywords: ["favipiravir"],
      checked: false,
      icon: ["fas", "capsules"]
    },
    Tocilizumab: {
      keywords: ["tocilizumab"],
      checked: false,
      icon: ["fas", "tablets"]
    },
    Plasma: {
      keywords: ["plasma"],
      checked: false,
      icon: ["fas", "tint"]
    },
    Food: {
      keywords: ["tiffin", "food"],
      checked: false,
      icon: ["fas", "utensils"]
    }
  };
  import { library } from "@fortawesome/fontawesome-svg-core";
  import { fas } from "@fortawesome/free-solid-svg-icons";
  import { requirementStore } from "./store.js";
  import { Col, Container, Row, Card } from "sveltestrap";
  import { FontAwesomeIcon } from "fontawesome-svelte";
  library.add(fas);
  function selectReq(element) {
    console.log(element);
    document.getElementById(element).children[0].checked = "checked";
  }
  var requirements = [];

  export function getRequirements() {
    //alsoSearchFor = Array(alsoSearchFor);
    //console.log(typeof alsoSearchFor);
    //console.log(aSF);
    var asfKeys = Object.keys(alsoSearchFor);
    requirements = asfKeys.map(key =>
      alsoSearchFor[key].checked ? alsoSearchFor[key].keywords.join(" ") : null
    );

    return requirements.join(" ").trim();
  }
</script>
    
    <Card>
<div style="margin:4%">

<h2>Requirements</h2>


<Container>

<Row cols="2">
	{#each Object.keys(alsoSearchFor) as item (item)}
		<Col>
    
    <div id={"select"+item} class='check' >
    <input on:click={getRequirements} bind:checked={alsoSearchFor[item].checked}  type="checkbox" />

    <FontAwesomeIcon icon={alsoSearchFor[item].icon} />
		<label for={`alsoSearchFor-${item}`}>{item}</label>
    </div>
    </Col>
	{/each}
</Row>

</Container>
</div>
    </Card>
