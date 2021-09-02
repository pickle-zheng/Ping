<script>
  import { user } from "./user";
  import { roomKey } from "./store";
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

  function makeid(length) {
    var result = "";
    var characters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
    var charactersLength = characters.length;
    for (var i = 0; i < length; i++) {
      result += characters.charAt(Math.floor(Math.random() * charactersLength));
    }
    return result;
  }
  function generateRoomKey() {
    const newRoomKey = makeid(5);
    roomKey.update((n) => newRoomKey);
  }

  function roomKeyChangeHandler() {
    console.log("changing room key to", roomKey_value);
    roomKey.update((n) => roomKey_value);
  }
</script>

<label for="roomKey">Room Key</label>
<select
  id="roomKey"
  name="roomKey"
  bind:value={roomKey_value}
  on:change={roomKeyChangeHandler}
>
  <option value="cpt">Creative Production Team</option>
  <option value="darkroom">Dark Room</option>
  <option value="general">General</option>
</select>

<label for="username">Username</label>
<input name="username" bind:value={username} minlength="3" maxlength="16" />

<label for="password">Password</label>
<input name="password" bind:value={password} type="password" />

<button class="login" on:click={login}>Login</button>
<button class="login" on:click={signup}>Sign Up</button>
