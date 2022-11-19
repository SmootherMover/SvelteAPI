<script>
  export let agentName = 1;
  
  const getAgent = async() => {
    let response = await fetch("https://valorant-api.com/v1/agents");
    let result = await response.json();
    if (response.ok){
      return result;
    }else{
      throw new Error(result);
    }
  };

  let userPromise = getAgent();
  console.log(userPromise);
  $: console.log(agentName);
  
</script>


{#await userPromise}
	<p>...waiting</p>
{:then agents}
  <li>
    <h3 id="name">{agents.data[agentName].displayName}</h3>
    <img src= {agents.data[agentName].fullPortrait} alt = "asd"/>
    <p><b style="color: black;">Description:</b> {agents.data[agentName].description}</p>
    <h3 style="text-align: center; color: black;"><b><u>Abilities</u></b></h3>
  </li>
{:catch error}
	<p style="color: red">{error.message}</p>
{/await}

<style>

#name{
  font-family: "VALORANT", sans-serif;
  color: black;
  font-size: 50px;
  margin-bottom: 0px;
}

img{
  background-color: white;
  width: 20vw;
  border: solid 5px black;
}

p{ 
  background-color: #FF4457;
}

h3{
  color: white;
  -webkit-text-stroke: 0.2px black;
  margin: 0;
  font-family: sans-serif;
  text-align: center; 
  
}


</style>