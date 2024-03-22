# perdoname
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>Fran, ¿me perdonas?</title>
<style>
  body {
    font-family: Arial, sans-serif;
    text-align: center;
    background-color: #3498db; /* Azul */
    color: white;
    margin: 0;
    padding: 0;
  }
  h1, button, #alertMessage {
    animation: pulse 1s infinite alternate;
  }
  @keyframes pulse {
    0% { transform: scale(1); }
    100% { transform: scale(1.1); }
  }
  button {
    font-size: 18px;
    padding: 10px 20px;
    margin: 10px;
    border-radius: 5px;
    cursor: pointer;
    transition: transform 0.3s ease, font-size 0.3s ease;
  }
  #siButton {
    background-color: #2980b9; /* Azul más oscuro */
    border: none;
  }
  #noButton {
    background-color: #c0392b; /* Rojo oscuro */
    border: none;
  }
  .animated-message {
    animation: move-message 2s ease-in-out infinite alternate;
  }
  @keyframes move-message {
    0% { transform: translateX(-20px); }
    100% { transform: translateX(20px); }
  }
  .animating-letters {
    display: inline-block;
    overflow: hidden;
    animation: animate-letters 2s infinite alternate;
  }
  @keyframes animate-letters {
    0% { transform: translateY(0); }
    100% { transform: translateY(-10px); }
  }
</style>
</head>
<body>
<h1>Fran, ¿me perdonas?</h1>
<button id="siButton">Sí</button>
<button id="noButton">No</button>

<script>
let noButtonClickCount = 0;

document.getElementById("noButton").addEventListener("click", function() {
  this.style.fontSize = `${18 - noButtonClickCount}px`;
  noButtonClickCount++;
});

document.getElementById("siButton").addEventListener("click", function() {
  showAlertMessage("¡Fran, sí! ¡Salgamos y celebremos!");
});

function showAlertMessage(message) {
  let alertMessage = document.createElement("div");
  alertMessage.textContent = "";

  for(let i = 0; i < message.length; i++) {
    let span = document.createElement("span");
    span.textContent = message[i];
    span.classList.add("animating-letters");
    alertMessage.appendChild(span);
  }

  alertMessage.id = "alertMessage";
  alertMessage.classList.add("animated-message");
  document.body.appendChild(alertMessage);

  // Trigger reflow to restart animation
  void alertMessage.offsetWidth;

  setTimeout(() => {
    alertMessage.remove();
  }, 3000);
}
</script>
</body>
</html>
