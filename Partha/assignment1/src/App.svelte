<script>
    import { Router, Route } from "svelte-routing";
    import Login from "./Components/Login.svelte";
    import Signup from "./Components/Signup.svelte";
    import Home from "./Components/Home.svelte";
</script>

<main>
    <Router>
        <Route path="/" component={Home} />
        <Route path="/Signup" component={Signup} />
        <Route path="/Login" component={Login} />
    </Router>	
</main>

<style>
    :global(body) {
        background-color: blueviolet;
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
