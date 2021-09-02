<script>
  import { user } from "../utils/user";
  import { roomKey } from "../utils/store";
  import RoomSelector from "../components/RoomSelector.svelte";
  let username;
  let password;
  let roomKey_value;

  roomKey.subscribe((value) => {
    roomKey_value = value;
  });

  function login() {
    user.auth(username, password, ({ err }) => err && alert(err));
  }
  function signup() {
    user.create(username, password, ({ err }) => {
      if (err) {
        alert(err);
      } else {
        login();
      }
    });
  }
</script>

<RoomSelector />

<label for="username">Username</label>
<input name="username" bind:value={username} minlength="3" maxlength="16" />

<label for="password">Password</label>
<input name="password" bind:value={password} type="password" />

<button class="login" on:click={login}>Login</button>
<button class="login" on:click={signup}>Sign Up</button>
