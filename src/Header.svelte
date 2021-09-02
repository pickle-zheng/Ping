<script>
  import { username, user } from "./user";
  import { roomKey } from "./store";

  let roomKey_value;
  function signout() {
    user.leave();
    username.set("");
  }
  roomKey.subscribe((v) => (roomKey_value = v));
</script>

<header>
  <h1>
    <img class="logo" src="assets/logo.png" alt="logo" />
    {#if $username}
      <span>Channel {roomKey_value}</span>
    {/if}
  </h1>
  {#if $username}
    <div class="user-bio">
      <span>Hello <strong>{$username}</strong></span>
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
