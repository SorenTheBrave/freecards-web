<script>

  const codeFormat = /^[a-zA-Z]{3}$/;
  export let joinName = "";
  export let lobbyCode = "";

  const joinLobby = () => {
    if(!joinName || !codeFormat.test(lobbyCode)) return; // validation here later

  };
  let showCreateModal = false;
</script>
<div class="columns-1 min-w-full">
  {#if showCreateModal}
    <create-lobby-modal/>
  {/if}
  <div id="banner" class="flex justify-around row px-4 md:py-14 lg:py-16 overflow-x-hidden min-h-fit">
    <h1 class="self-center text-2xl sm:text-4xl md:text-7xl xl:text-8xl">Any&nbsp;card&nbsp;game. Free&nbsp;with&nbsp;friends.</h1>
  </div>
  <div class="flex flex-col columns-3xs justify-around items-center">
    <div id=create class="bg-slate-500 border border-white rounded-md main-menu-item text-center">
      <h2 class="flex-col font-sans text-black font-bold">New lobby</h2>
      <button on:click="{() => showCreateModal = true}" class="bg-blue-800 font-white font-bold rounded-sm">Create a new lobby!</button>
    </div>
    <div id=join class="bg-slate-500 border border-white rounded-md main-menu-item">
      <h2 class="flex-col font-sans text-black font-bold">Join lobby by code</h2>
      <label for=name-input>Name: (2+ characters):</label><input id=name-input type=text placeholder="Enter a name..." bind:value={joinName}/>
      <label for=code-input>Lobby Code (3 letters):</label><input id=code-input type=text placeholder="ABC" bind:value={lobbyCode}/>
      <button on:click="{joinLobby}" class="bg-emerald-800 font-white font-bold rounded-sm">Join Game!</button>
    </div>
  </div>
</div>

<style>
div#banner {
  background-image: none; /* Get bg image of poker table felt texture*/
  justify-content: space-around;
  display: flex;
}
div.main-menu-item {
  min-width: 30rem;
  display: inline-flex;
  flex-direction: row;
}
h1{
  max-width: 70%;
  width: clamp(50%,60%,80%);
}
</style>