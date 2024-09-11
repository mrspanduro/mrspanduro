<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Salón Janeth Zazueta - Iniciar Sesión</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .login-container {
            background-color: #fff;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            width: 300px;
            text-align: center;
        }
        .login-container h2 {
            margin-bottom: 20px;
            color: #333;
        }
        .form-group {
            margin-bottom: 15px;
            text-align: left;
        }
        .form-group label {
            display: block;
            margin-bottom: 5px;
            color: #555;
        }
        .form-group input {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            box-sizing: border-box;
        }
        .form-group button {
            width: 100%;
            padding: 10px;
            background-color: #28a745;
            color: #fff;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
        }
        .form-group button:hover {
            background-color: #218838;
        }
        .error-message {
            color: red;
            display: none;
            margin-bottom: 10px;
        }
    </style>
</head>
<body>
    <div class="login-container">
        <h2>Iniciar Sesión</h2>
        <form id="loginForm">
            <div class="form-group">
                <label for="username">Usuario:</label>
                <input type="text" id="username" name="username" required>
            </div>
            <div class="form-group">
                <label for="password">Contraseña:</label>
                <input type="password" id="password" name="password" required>
            </div>
            <div class="error-message" id="error-message">Usuario o contraseña incorrectos.</div>
            <div class="form-group">
                <button type="submit">Ingresar</button>
            </div>
        </form>
    </div>

    <script>
        document.getElementById('loginForm').addEventListener('submit', function(event) {
            event.preventDefault(); // Previene el envío del formulario

            // Obtén los valores del usuario y contraseña
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;

            // Validar el usuario y contraseña (esto es solo un ejemplo; debes implementar tu lógica)
            if (username === 'admin' && password === '12345') {
                alert('Inicio de sesión exitoso');
                // Redirigir a la página principal o al panel de control
                window.location.href = 'dashboard.html'; // Asegúrate de tener una página llamada dashboard.html
            } else {
                // Mostrar mensaje de error
                document.getElementById('error-message').style.display = 'block';
            }
        });
    </script>
</body>
</html>
