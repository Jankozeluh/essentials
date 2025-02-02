<script>
  import { writable } from 'svelte/store';

  let username = '';
  let password = '';
  let error = writable('');

  async function handleLogin() {
    try {
      const response = await fetch('http://localhost:8000/login', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        credentials: 'include',
        body: JSON.stringify({ username, password })
      });

      if (!response.ok) {
        const data = await response.json();
        error.set(data.detail || 'Login failed');
        return;
      }

      window.location.href = '#/';
    } catch (e) {
      error.set('Network error occurred');
      console.error('Login error:', e);
    }
  }
</script>

<div class="login-container">
  <h2>Login</h2>
  
  {#if $error}
    <div class="error">{$error}</div>
  {/if}

  <form on:submit|preventDefault={handleLogin}>
    <div class="form-group">
      <label for="username">Username</label>
      <input
        type="text"
        id="username"
        bind:value={username}
        required
      />
    </div>

    <div class="form-group">
      <label for="password">Password</label>
      <input
        type="password"
        id="password"
        bind:value={password}
        required
      />
    </div>

    <button type="submit">Login</button>
  </form>
</div>

<style>
  .login-container {
    max-width: 400px;
    margin: 2rem auto;
    padding: 2rem;
    border: 1px solid #ddd;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  h2 {
    text-align: center;
    color: #333;
    margin-bottom: 1.5rem;
  }

  .form-group {
    margin-bottom: 1rem;
  }

  label {
    display: block;
    margin-bottom: 0.5rem;
    color: #555;
  }

  input {
    width: 100%;
    padding: 0.5rem;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-size: 1rem;
  }

  button {
    width: 100%;
    padding: 0.75rem;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 4px;
    font-size: 1rem;
    cursor: pointer;
  }

  button:hover {
    background-color: #45a049;
  }

  .error {
    color: #dc3545;
    margin-bottom: 1rem;
    text-align: center;
  }
</style>