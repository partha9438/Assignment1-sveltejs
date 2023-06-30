<script>
    import { onMount } from "svelte";
    import { navigate } from "svelte-routing";
    let username = "";
    let password = "";

    function handleLogin() {
        const storedUsername = localStorage.getItem("username");
        const storedPassword = localStorage.getItem("createpassword");
        const isLoggedIn = username === storedUsername && password === storedPassword;

        if (isLoggedIn) {
            localStorage.setItem("isLoggedIn", "true"); 
            navigate("/"); 
        } else {
            alert("Invalid username or password");
        }
    }

    function goToSignup() {
        navigate("/Signup"); 
    }
    onMount(() => {
    const link = document.getElementById("signup-link");

    link.addEventListener("click", (event) => {
    event.preventDefault();
    goToSignup();
    });
  });
</script>

<main>
    <div id="form-border">
        <form on:submit|preventDefault={handleLogin}>
            <h1 id="login">Login</h1>
            <hr/>
            <div>
        <input type="text" bind:value={username} id="username" placeholder="Username" required/>
            </div>
            <div>
        <input type="password" bind:value={password} id="password" placeholder="Password" required/>
            </div>
        <p><a href="forgot password">Forgot password?</a></p>
            <div>
        <button type="submit" id="login-button">Login</button>
            </div>
        </form>
        <p>
            Not a member ? <a href="/Signup" id="signup-link">Sign up here.</a>
        </p>
    </div>
</main>

<style>
       main {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }
      
    input {
        margin-top: 30px;
        border: none;
        border-bottom: 1px solid black;
        outline: none;
        background-color: transparent;
        width: 85%
    }

    #login-button {
        width: 80%;
        padding: 7px;
        /* background-color: #94cbf8; */
        background-color: rgb(71, 152, 255);
        color: white;
        border-radius:20px;
        cursor: pointer;
    }

    hr {
        border: none;
        height: 2px;
        background-color: #000;
        width: auto;
    }

    #form-border{
            width: 30%;
            border-radius:20px;
            background-color: white;
            height: 70%;
        }	
    #login {
        color: black;
        margin-bottom: 30px;
        font-weight: bold;
    }

    main {
        text-align: center;
        padding: 1em;
        max-width: 240px;
        margin: 0 auto;
    }

    @media (min-width: 640px) {
        main {
            max-width: none;
        }
    }
</style>
