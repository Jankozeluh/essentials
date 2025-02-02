<script>
  import { onMount } from 'svelte';
  import { writable } from 'svelte/store';
  import Router from "svelte-spa-router";
  import routes from "./routes";

  let isAuthenticated = writable(false);

  async function checkAuth() {
    try {
      const response = await fetch(`http://localhost:8000/validate-token`, {
        method: "POST",
        credentials: "include",
      });

      if (!response.ok) {
        console.error("User is not authenticated.");
        return false;
      }

      const data = await response.json();
      console.log("User is authenticated:", data);
      return true;
    } catch (e) {
      console.error("Error checking authentication:", e);
      return false;
    }
  }

  async function logout() {
    try {
      await fetch("http://localhost:8000/logout", {
        method: "POST",
        credentials: "include",
      });

      isAuthenticated.set(false);
      window.location.href = "#/";
    } catch (error) {
      console.error("Logout failed:", error);
    }
  }

  onMount(async () => {
    isAuthenticated.set(await checkAuth());
  });
</script>

<main>
  <Router {routes} />
</main>

<style>
  main {
    width: 100%;
    height: 100%;
    padding: 1rem;
  }
</style>