<script>
  import UserGrid from './lib/UserGrid.svelte';
  import Profile from './lib/Profile.svelte';
  import PendingRequests from './lib/PendingRequests.svelte';
</script>

<main>
  <img src="skillswap.png" alt="Skill Swap" />
  <Profile />
  <UserGrid />
  <PendingRequests />
</main>

<style>
  h1 {
    position: fixed;
    top: 0;
    left: 0;
    padding: 10px;
    margin: 0;
    background-color: white;
    z-index: 10;
  }

  main {
    font-family: Arial, sans-serif;
    margin-top: 50px;
    padding: 16px;
  }

  img {
    width: 200px;
    position: fixed;
    top: 0px;
    left: 0px;
    padding: 20px;
  }
</style>
