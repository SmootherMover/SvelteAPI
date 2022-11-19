<script>
	import Navbar from "./lib/Navbar.svelte"
  import Input from "./lib/Input.svelte"
  
  let agentName;
  const searchAgent = () => {
    agentName = Math.floor(Math.random() * 21);
    if(agentName == 7){
      agentName = 8;
    }
  } 

  const agentList = {
  "fade": 0,
  "breach": 1,
  "raze": 2,
  "chamber": 3,
  "kay/o": 4,
  "skye": 5,
  "cypher": 6,
  "sova": 8,
  "killjoy": 9,
  "harbor": 10,
  "viper": 11,
  "phoenix": 12,
  "astra": 13,
  "brimstone": 14,
  "neon": 15,
  "yoru": 16,
  "sage": 17,
  "reyna": 18,
  "omen": 19,
  "jett": 20,
};

</script>

<Navbar />

<button on:click = {searchAgent}>
  Random Agent
</button>

<Input {agentName} />



<style>
	
</style>