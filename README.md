<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chat Box y Alertas</title>
    <style>
        body {
            background: transparent;
        }
        #chat-box {
            width: 300px;
            height: 400px;
            overflow-y: auto;
            padding: 10px;
            border: 2px solid #ff80ff;
            border-radius: 10px;
            background: rgba(50, 10, 70, 0.8);
            box-shadow: 0 0 10px #ff00ff;
            color: white;
            font-family: Arial, sans-serif;
            position: absolute;
            bottom: 20px;
            right: 20px;
        }
        .chat-message {
            padding: 5px;
            margin: 5px 0;
            border-radius: 5px;
            background: rgba(255, 128, 255, 0.6);
            animation: fadeIn 0.5s ease-in-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .alert {
            position: absolute;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            padding: 15px;
            background: linear-gradient(45deg, #ff00ff, #ff80ff);
            border-radius: 10px;
            box-shadow: 0 0 15px #ff00ff;
            color: white;
            font-size: 20px;
            display: none;
            animation: popIn 0.5s ease-in-out;
        }
        @keyframes popIn {
            from { transform: translate(-50%, -10px) scale(0.9); opacity: 0; }
            to { transform: translate(-50%, 0) scale(1); opacity: 1; }
        }
    </style>
</head>
<body>
    <div id="chat-box"></div>
    <div id="alert" class="alert">¡Nueva Alerta!</div>

    <script>
        function addMessage(user, message) {
            const chatBox = document.getElementById("chat-box");
            const messageElement = document.createElement("div");
            messageElement.classList.add("chat-message");
            messageElement.innerHTML = `<strong>${user}:</strong> ${message}`;
            chatBox.appendChild(messageElement);
            chatBox.scrollTop = chatBox.scrollHeight;
        }

        function showAlert(text) {
            const alertBox = document.getElementById("alert");
            alertBox.textContent = text;
            alertBox.style.display = "block";
            setTimeout(() => {
                alertBox.style.display = "none";
            }, 3000);
        }

        // Simulación de mensajes y alertas
        setTimeout(() => addMessage("Viewer1", "¡Hola, qué bonito stream! 💜"), 1000);
        setTimeout(() => showAlert("¡Nuevo seguidor! 🌸"), 3000);
        setTimeout(() => addMessage("Viewer2", "¡Me encanta el diseño! 🌟"), 5000);
    </script>
</body>
</html>
