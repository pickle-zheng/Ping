<script>
  import { Link } from "svelte-navigator";
  import { username, user } from "../utils/user";
  import { roomKey } from "../utils/store";
  import RoomSelector from "../components/RoomSelector.svelte";

  let roomKey_value;
  function signout() {
    user.leave();
    username.set("");
  }
  roomKey.subscribe((v) => (roomKey_value = v));
</script>

<header>
  <div class="logoWrapper">
    <Link to="/"><img class="logo" src="assets/logo.png" alt="logo" /></Link>
    {#if $username}
      <RoomSelector />
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
