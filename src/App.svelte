<script>
  import Welcome from './Welcome.svelte';
  import Lobby from './Lobby.svelte';
  import { fly } from 'svelte/transition';

  const codeFormat = /^[a-zA-Z]{3}$/;

  let joinName = "";
  let lobbyCode = ""; // three-letter lobby code indicating which lobby the player is in
  let ws; // will store our lobby WebSocket connection
  let showLobby = false;
  //$: showLobby = (typeof joinName === 'string' && joinName.length > 1) && codeFormat.test(lobbyCode) && true; // ws; // just a stub for now...
  $: props = {joinName,lobbyCode,ws};
  const toggleShowLobby = () => showLobby=!showLobby;
</script>

<div id=main>
  {#if showLobby}
    <div id=lobby transition:fly={{x:250,duration:200}}>
      <Lobby {...props}></Lobby>
    </div>
  {:else}
    <div id=welcome transition:fly={{x:-250,duration:150}}>
      <Welcome {joinName} {lobbyCode}></Welcome>
    </div>
  {/if}
</div>
<button on:click="{toggleShowLobby}" class="min-h"></button>
<style>
div#main{
  display: flex;
  flex-direction: column;
  padding: 0;
  width: clamp(70%,40rem,90%);
  margin-inline: auto;
}
</style>
