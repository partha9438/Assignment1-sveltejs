<script>
     import { navigate } from "svelte-routing";
    let signupTitle = "ignUp";
    
    $: lowercaseTitle = signupTitle.toLowerCase();
    let username = "";
    let createpassword = "";
    let confirmpassword=""
  
    function handleSignup() {
        if (createpassword !== confirmpassword) {
      alert("Password and Confirm Password do not match");
      return;
    }
      localStorage.setItem("username", username);
      localStorage.setItem("createpassword", createpassword);
      localStorage.setItem("confirmpassword",confirmpassword)
      navigate("/Login")
    }
    </script>
    
    <main>
        <div id="form-border">
            <form on:submit|preventDefault={handleSignup}>
                <h1 id="sign">S{signupTitle}</h1>
                <hr/>
                <div>
                <input type="text" bind:value={username} id="username" placeholder="Username" required/>
                </div>
                <div>
                <input type="password" bind:value={createpassword} id="createpassword" placeholder="Create Password" required/>
                </div>
                <div>
                <input type="password" bind:value={confirmpassword} id="confirmpassword"placeholder="ConfirmPassword" required />
                </div>
              
                <button type="submit" id="login-button">SignUp</button>
              </form>
            
              
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
  border: none;
  border-bottom: 1px solid black;
  outline: none;
  background-color: transparent;
  width: 85%;
  margin-top: 30px;
}
        
        #login-button{
            width: 30%;
            padding: 7px ;
            background-color: #94cbf8;
            color: white;
            border-radius:20px ;
            cursor: pointer;
            margin-top: 20px;
        }
         hr {
        border: none;
        height: 2px;
        background-color: #000;
         width: auto;
      }
        #form-border{
            width: 35%;
            border: 2px solid black;
            border-radius:20px;
            background-color: white;
            height: 70%;
        }	
        #sign{
            color: black;
            margin-bottom: 30px;
            font-weight: bold;
        }
        :global(body){
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