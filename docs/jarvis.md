# Chat with J.A.R.V.I.S.

<label>User: <input id="user" value="wolfgang" /></label><br>
<label>Mode: <input id="mode" value="sassy" /></label><br>
<label>Model: <input id="model" value="gpt-4o" /></label><br>
<textarea id="input" rows="4" cols="50" placeholder="Type your message here..."></textarea><br>
<button onclick="sendMessage()">Send</button>

<pre id="response" style="white-space: pre-wrap; background: #f0f0f0; padding: 1em;"></pre>

<script>
  async function sendMessage() {
    const userId = document.getElementById("user").value;
    const input = document.getElementById("input").value;
    const mode = document.getElementById("mode").value;
    const model = document.getElementById("model").value;

    const res = await fetch("https://your-fly-app.fly.dev/chat", {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({ userId, input, mode, model })
    });
    const data = await res.json();
    document.getElementById("response").textContent = data.response;
  }
</script>