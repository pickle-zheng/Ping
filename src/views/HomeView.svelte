<script>
  import { Link } from "svelte-navigator";
</script>

<div class="app">
  <header>
    <nav class="logoWrapper">
      <Link to="/"><img class="logo" src="assets/logo.png" alt="logo" /></Link>
    </nav>
  </header>
  <main style="background-color: grey; color: black">
    <p />
    <p>Welcome to Ping</p>
    <p>Ping is a decentralised chat app.</p>
    <p>
      Just like how cryto currency works. None of the messages lives in a single
      server.
    </p>
    <p>
      All the messages are fully encrypted, only the members of the channel
      would have the key to decrypt and read the messages.
    </p>
    <Link to="chat"><button>Start "Ping"ing</button></Link>
  </main>
</div>
