<script>
    // conexão com backend
    //input login
    //input de password
    // botão de login
    // botão de registro
    let email = "";
    let password = "";
    let error = "";

    async function handleLogin() {
        const data = { email, password };
        const response = await fetch("localhost:8080/login", {
            method: "POST",
            body: JSON.stringify(data),
        });

        if (response.ok) {
            console.log("Login válido");
        } else {
            error = "Login inválido";
        }
    }

    async function handleRegister() {
        const data = { email, password };
        const response = await fetch("localhost:8080/registro", {
            method: "POST",
            body: JSON.stringify(data),
        });

        if (response.ok) {
            console.log("Registro válido");
        } else {
            error = "Login inválido";
        }
    }
</script>

<body>
    <div class="container">
        <h1>Autenticação</h1>
        <label for="email">Email:</label>
        <input bind:value={email} type="text" id="email" />
        <label for="password">password:</label>
        <input bind:value={password} type="password" id="password" />
        <div class="btn">
            <button class="login" on:click={handleLogin}>Login</button>
            <button class="register" on:click={handleRegister}
                >Registrar</button
            >
        </div>
        {#if error}
            <p>{error}</p>
        {/if}
    </div>
</body>

<style>
    * {
        font-family: Verdana, Geneva, Tahoma, sans-serif;
    }

    body {
        margin: 0;
        padding: 0;
        width: 100vw;
        height: 100vh;
        overflow: hidden;
        display: flex;
        justify-content: center;
        align-items: center;
        box-sizing: border-box;
    }

    .container {
        text-align: center;
        display: flex;
        flex-direction: column;
        padding: 64px;
        background: rgba(182, 184, 183, 0.493);
        width: 300px;
        height: 300px;
        border-radius: 15px;
        box-shadow: 5px 15px 45px rgba(0, 0, 0, 0.26);
    }

    h1 {
        font-family: Verdana, Geneva, Tahoma, sans-serif;
        text-align: center;
        color: rgb(0, 89, 255);
        text-shadow: 0px 5px 10px rgba(0, 0, 0, 0.192);
    }

    label {
        justify-content: center;
        font-weight: bold;
        padding-bottom: 8px;
        padding-top: 8px;
    }

    input {
        border: none;
        height: 24px;
        border-radius: 10px;
    }

    .btn {
        padding: 8px;
        justify-content: center;
    }

    .login {
        border: none;
        border-radius: 15px;
        background-color: rgb(0, 89, 255);
        padding: 8px 16px;
        margin-right: 8px;
    }

    .register {
        border: none;
        border-radius: 15px;
        background-color: rgb(255, 255, 255);
        padding: 8px 16px;
    }

    .login:hover {
        background-color: rgba(0, 89, 255, 0.3);
        cursor: pointer;
    }

    .register:hover {
        background-color: aliceblue;
        cursor: pointer;
    }
</style>
