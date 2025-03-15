<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chatbot</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; margin: 20px; }
        #chat-container { width: 300px; margin: auto; border: 1px solid #ccc; padding: 10px; }
        #messages { height: 200px; overflow-y: auto; border-bottom: 1px solid #ccc; padding: 5px; }
        input, button { margin-top: 10px; }
    </style>
</head>
<body>
    <h1>Chatbot</h1>
    <div id="chat-container">
        <div id="messages"></div>
        <input type="text" id="user-input" placeholder="Escribe un mensaje...">
        <button onclick="sendMessage()">Enviar</button>
    </div>

    <script>
        async function sendMessage() {
            const input = document.getElementById("user-input");
            const message = input.value.trim();
            if (message === "") return;
            
            // Mostrar mensaje del usuario
            const messagesDiv = document.getElementById("messages");
            messagesDiv.innerHTML += `<p><strong>Tú:</strong> ${message}</p>`;
            input.value = "";

            try {
                const response = await fetch("http://localhost:8080/chat", {
                    method: "POST",
                    headers: { "Content-Type": "application/json" },
                    body: JSON.stringify({ message })
                });
                const data = await response.json();
                messagesDiv.innerHTML += `<p><strong>Bot:</strong> ${data.response}</p>`;
            } catch (error) {
                messagesDiv.innerHTML += `<p style="color:red;"><strong>Error:</strong> No se pudo conectar al chatbot.</p>`;
            }
            messagesDiv.scrollTop = messagesDiv.scrollHeight;
        }
    </script> 
<!-- Start of HubSpot Embed Code -->
  <script type="text/javascript" id="hs-script-loader" async defer src="//js-na1.hs-scripts.com/49545840.js"></script>
<!-- End of HubSpot Embed Code -->
</body>
</html>
