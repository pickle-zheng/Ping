<script>
  import { roomKey } from "../utils/store";
  let roomKey_value;
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

<!-- <label for="roomKey">Room Key</label> -->
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
