<script>
  import { navigate } from "svelte-routing";

  function goToLogin() {
    navigate("/Login");
  }
  function goToSignup() {
    navigate("/Signup");
  }
  let isLoggedIn = false;
  if (localStorage.getItem("isLoggedIn") === "true") {
    isLoggedIn = true;
    console.log("isLoggedIn:", isLoggedIn);
  } else {
    navigate("/Login");
  }
</script>

<main >
{#if isLoggedIn}
  <h1 id="home">Welcome to the Home Page!</h1>
{/if}
<p>If you already have an account, <button id="gotologin" on:click={goToLogin}>Login</button></p>
<p>If you don't have an account yet, <button id="gotosignup" on:click={goToSignup}>Sign Up</button></p>
</main>

<style>
  main{
    background-color: chartreuse;
  }
  #home {
      display: flex;
      justify-content: center;
  }
  #gotologin{
    border: 2px solid black;
    border-radius: 10px;
    cursor: pointer;
  }
  #gotosignup{
    border: 2px solid black;
    border-radius: 10px;
    cursor: pointer;
  }
</style>
