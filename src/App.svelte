<script>
  import { Router, Route, Link } from "svelte-navigator";
  import ChatView from "./views/ChatView.svelte";
  import HomeView from "./views/HomeView.svelte";
</script>

<Router>
  <div class="home">
    <Route path="chat">
      <ChatView />
    </Route>

    <Route path="/">
      <HomeView />
    </Route>
  </div>
</Router>
