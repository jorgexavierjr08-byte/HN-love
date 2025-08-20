# HN-love from flask import Flask, render_template

app = Flask(__name__)

@app.route("/")
def home():
    return render_template("index.html")

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
flask
gunicorn
web: gunicorn app:app
<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <title>HN Amor</title>
    <link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
</head>
<body>
    <div class="container">
        <img src="{{ url_for('static', filename='images/bear.png') }}" alt="Ursinho" class="bear">
        <h1>Com muito carinho 💖</h1>
        <button onclick="playVoice()">Ouvir mensagem</button>
    </div>

    <script src="{{ url_for('static', filename='script.js') }}"></script>body {
    background: #ffe6f0;
    text-align: center;
    font-family: Arial, sans-serif;
}

.container {
    margin-top: 50px;
}

.bear {
    width: 200px;
}

button {
    padding: 10px 20px;
    border: none;
    border-radius: 20px;
    background: #ff6699;
    color: white;
    font-size: 16px;
    cursor: pointer;
}
button:hover {
    background: #cc3366;
}
function playVoice() {
    const msg = new SpeechSynthesisUtterance("Olá, este é o site do HN, feito com muito carinho para ti.");
    msg.lang = "pt-PT";
    msg.rate = 1;
    msg.pitch = 1.2;
    msg.voice = speechSynthesis.getVoices().find(voice => voice.name.includes("female")) || null;
    speechSynthesis.speak(msg);
}
</body>
</html>
