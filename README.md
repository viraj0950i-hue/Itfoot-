# Itfoot-
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>JARVIS AI</title>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  background: #07111f;
  color: white;
  font-family: Arial, sans-serif;
}

header {
  text-align: center;
  padding: 22px;
  border-bottom: 1px solid #17466b;
}

header h1 {
  color: #32baff;
  letter-spacing: 5px;
  margin: 5px;
}

.status {
  color: #39e89a;
  font-size: 12px;
}

.container {
  max-width: 600px;
  margin: auto;
  padding: 18px;
}

.core {
  width: 135px;
  height: 135px;
  margin: 25px auto;
  border: 3px solid #27baff;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 0 30px #1689cc;
  animation: pulse 2s infinite;
}

.core span {
  font-size: 45px;
}

@keyframes pulse {
  50% {
    box-shadow: 0 0 55px #27baff;
  }
}

h2 {
  text-align: center;
  color: #32baff;
}

#chat {
  height: 280px;
  overflow-y: auto;
  border: 1px solid #1a4260;
  border-radius: 12px;
  padding: 12px;
  background: #0c1b2b;
}

.message {
  padding: 11px;
  margin: 9px 0;
  border-radius: 10px;
  line-height: 1.5;
  overflow-wrap: anywhere;
}

.user {
  background: #124e75;
  text-align: right;
}

.bot {
  background: #172c40;
}

.controls {
  display: flex;
  gap: 8px;
  margin-top: 12px;
}

input {
  flex: 1;
  min-width: 0;
  padding: 13px;
  border-radius: 8px;
  border: 1px solid #2586bd;
  background: #102238;
  color: white;
  font-size: 15px;
}

button {
  background: #087ebc;
  border: none;
  color: white;
  border-radius: 8px;
  padding: 12px;
  font-size: 15px;
  cursor: pointer;
}

button:active {
  background: #07547c;
}

.voice {
  display: block;
  width: 100%;
  margin-top: 12px;
  background: #126b5a;
}

.features {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  margin-top: 25px;
}

.feature {
  background: #102238;
  border: 1px solid #1c5276;
  padding: 18px 10px;
  text-align: center;
  border-radius: 10px;
}

.feature span {
  display: block;
  font-size: 25px;
  margin-bottom: 8px;
}

footer {
  text-align: center;
  color: #7792a9;
  padding: 20px;
  font-size: 12px;
}
</style>
</head>

<body>

<header>
  <h1>J.A.R.V.I.S.</h1>
  <div class="status">● SYSTEM ONLINE</div>
</header>

<div class="container">

  <div class="core">
    <span>🤖</span>
  </div>

  <h2>Hello, Sir.</h2>
  <p style="text-align:center;color:#8faec5">
    Your Personal AI Assistant
  </p>

  <h3>AI CONVERSATION</h3>

  <div id="chat">
    <div class="message bot">
      JARVIS: Hello Sir! I am ready. How can I help you?
    </div>
  </div>

  <div class="controls">
    <input id="userInput"
      placeholder="Ask JARVIS anything..."
      onkeydown="if(event.key==='Enter') sendMessage()">

    <button onclick="sendMessage()">Send</button>
  </div>

  <button class="voice" onclick="startVoice()">
    🎤 TALK TO JARVIS
  </button>

  <h3>CONTROL CENTER</h3>

  <div class="features">
    <div class="feature">
      <span>🧠</span>
      AI Assistant
    </div>

    <div class="feature">
      <span>📍</span>
      Family Location
    </div>

    <div class="feature">
      <span>🛡️</span>
      Home Security
    </div>

    <div class="feature">
      <span>📹</span>
      CCTV System
    </div>

    <div class="feature">
      <span>🏠</span>
      Smart Home
    </div>

    <div class="feature">
      <span>⚙️</span>
      Settings
    </div>
  </div>

</div>

<footer>
  PROJECT JARVIS | VERSION 1.0<br>
  Personal AI Assistant
</footer>

<script>
const chat = document.getElementById("chat");
const input = document.getElementById("userInput");

function addMessage(message, type) {
  const div = document.createElement("div");
  div.className = "message " + type;
  div.textContent = message;
  chat.appendChild(div);
  chat.scrollTop = chat.scrollHeight;
}

function getReply(question) {
  const q = question.toLowerCase();

  if (q.includes("hello") || q.includes("hi") ||
      q.includes("नमस्ते")) {
    return "Hello Sir! JARVIS is ready to assist you.";
  }

  if (q.includes("your name") || q.includes("नाम")) {
    return "Sir, I am JARVIS, your personal assistant.";
  }

  if (q.includes("time") || q.includes("समय")) {
    return "Current time is " +
      new Date().toLocaleTimeString();
  }

  if (q.includes("date") || q.includes("तारीख")) {
    return "Today's date is " +
      new Date().toLocaleDateString();
  }

  if (q.includes("how are you")) {
    return "I am functioning perfectly, Sir.";
  }

  if (q.includes("jarvis")) {
    return "Yes Sir! I am listening.";
  }

  return "Sir, I received your message. My AI connection is not configured yet. This is currently my offline demo mode.";
}

function speak(message) {
  if (!("speechSynthesis" in window)) return;

  window.speechSynthesis.cancel();

  const speech = new SpeechSynthesisUtterance(message);
  speech.lang = "en-IN";
  speech.rate = 0.95;

  window.speechSynthesis.speak(speech);
}

function sendMessage() {
  const question = input.value.trim();

  if (!question) return;

  addMessage("You: " + question, "user");

  const reply = getReply(question);

  setTimeout(() => {
    addMessage("JARVIS: " + reply, "bot");
    speak(reply);
  }, 400);

  input.value = "";
}

function startVoice() {
  const SpeechRecognition =
    window.SpeechRecognition ||
    window.webkitSpeechRecognition;

  if (!SpeechRecognition) {
    alert("Voice recognition is not supported in this browser. Try Chrome.");
    return;
  }

  const recognition = new SpeechRecognition();

  recognition.lang = "hi-IN";
  recognition.continuous = false;
  recognition.interimResults = false;

  recognition.onstart = () => {
    addMessage("JARVIS: Listening, Sir...", "bot");
  };

  recognition.onresult = (event) => {
    const speechText =
      event.results[0][0].transcript;

    input.value = speechText;
    sendMessage();
  };

  recognition.onerror = () => {
    addMessage("JARVIS: Voice recognition error. Please try again.", "bot");
  };

  recognition.start();
}
</script>

</body>
</html>
