<script>
	import Navbar from "./lib/Navbar.svelte"
  import Info from "./lib/Info.svelte"

  let agentID;
  let show;  
  let input = "";

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

  const randomID = () => {
    agentID = Math.floor(Math.random() * 21);
    show = true;
    if(agentID == 7){
      agentID = 8;
    };
    input = getObjKey(agentList, agentID);
  };

  console.log(agentList["fade"])
  const getObjKey = (obj, val) => Object.keys(obj).find(key => obj[key] === val);
    
  const searchAgent = () => {
    if(agentList[input.toLowerCase()]){
      agentID = agentList[input.toLowerCase()];
      show = true;
      console.log(agentID);
    }else if(agentList[input.toLowerCase()] == 0){
      agentID = 0;
      show = true;    
    }else{
      show = false;
    };
  };

</script>

<Navbar />
<div>
<button on:click = {randomID}>
  Random Agent
</button>
<input maxlength = "10" bind:value={input} on:input={searchAgent}>
</div>
<Info {agentID} {show} {input} />


<style>
  div{
    margin-top: 10px;
  }
  button{
    padding: 10px;
    background-color: peach;
    border-radius: 10px;
    color: black;
    transition-duration: 0.1s;
  }

  button:hover{
    background-color: #FF4457;
    box-shadow: 0 12px 16px 0 rgba(0,0,0,0.24), 0 17px 50px 0 rgba(0,0,0,0.19);
    color:white;
  }

  input{
    font-family: "VALORANT", sans-serif;
    border-radius: 10px;
    padding: 10px;
  }
</style>