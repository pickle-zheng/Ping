<script>
  import { username, user } from "./user";
  import { roomKey } from "./store";
  import RoomSelector from "./RoomSelector.svelte";

  let roomKey_value;
  function signout() {
    user.leave();
    username.set("");
  }
  roomKey.subscribe((v) => (roomKey_value = v));
</script>

<header>
  <div class="logoWrapper">
    <img class="logo" src="assets/logo.png" alt="logo" />
    {#if $username}
      <RoomSelector/>
    {/if}
  </div>
  {#if $username}
    <div class="user-bio">
      <img
        class="avartar"
        src={`https://avatars.dicebear.com/api/initials/${$username}.svg`}
        alt="avatar"
      />
    </div>

    <button class="signout-button" on:click={signout}>Sign Out</button>
  {:else}
    <h3>Powered By Gun.js</h3>
  {/if}
</header>
