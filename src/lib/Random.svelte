<script>
  export let agentID;
  export let show;
  export let input;

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
  console.log(Object.entries(userPromise));
</script>

<h2>{input}</h2>
{#if show}
{#await userPromise}
  <p>Waiting</p>
{:then agents}
  <li style="list-style-type: none;">
    <img src= {agents.data[agentID].fullPortrait} alt = "asd"/>
    <p><b style="color: black;">Description:</b> {agents.data[agentID].description}</p>
    <h3 style="text-align: center; color: black;"><b><u>Abilities</u></b></h3>
    <p class="abilities"><b>{agents.data[agentID].abilities[0].displayName}:</b> {agents.data[agentID].abilities[0].description}</p>
    <p class="abilities"><b>{agents.data[agentID].abilities[1].displayName}:</b> {agents.data[agentID].abilities[1].description}</p>
    <p class="abilities"><b>{agents.data[agentID].abilities[2].displayName}:</b> {agents.data[agentID].abilities[2].description}</p>
    <p class="abilities"><b>{agents.data[agentID].abilities[3].displayName}:</b> {agents.data[agentID].abilities[3].description}</p>
  </li>
{:catch error}
	<p style="color: red">{error.message}</p>
{/await}
{/if}


<style>
h2{
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