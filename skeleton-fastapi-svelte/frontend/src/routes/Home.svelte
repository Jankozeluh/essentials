<script>
  import { getContext } from 'svelte';

  let isAuthenticated = getContext('isAuthenticated');
</script>

<div class="container">
  <h1>Welcome to Svelte + FastAPI Template</h1>
  <p>This is a minimal, production-ready template for building web applications.</p>
  
  {#if $isAuthenticated}
    <p>You are logged in!</p>
  {:else}
    <a href="#/login">Login</a>
  {/if}
</div>

<style>
  .container {
    max-width: 800px;
    margin: 0 auto;
    padding: 2rem;
    text-align: center;
  }

  h1 {
    color: #333;
    margin-bottom: 1rem;
  }

  a {
    color: #4CAF50;
    text-decoration: none;
  }

  a:hover {
    text-decoration: underline;
  }
</style>