
<html lang="ms">
<head>
  <meta charset="UTF-8">
  <title>Cuba sekali</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 40px;
      text-align: center;
    }
    button {
      padding: 10px 20px;
      font-size: 16px;
    }
    #output {
      margin-top: 20px;
      font-size: 18px;
      color: #333;
    }
  </style>
</head>
<body>
  <h2>🎤 Sila sebut ayat (contoh: “jumpa lagi”, “selamat pagi”)</h2>
  <button onclick="startListening()">Mula Dengar</button>
  <p id="output"></p>

  <script>
    const phrases = {
      "jumpa lagi": "https://www.figma.com/proto/qv2LYsbEHpDjXtkTnpOnlP/Untitled--Copy-?node-id=29-302&t=JCiDsIBgDx0fdHdi-1", // contoh pautan
      "selamat pagi": "https://www.figma.com/proto/qv2LYsbEHpDjXtkTnpOnlP/Untitled--Copy-?node-id=29-169&t=er3c4XTsWvRlomlR-1"
    };

    function startListening() {
      const recognition = new (window.SpeechRecognition || window.webkitSpeechRecognition)();
      recognition.lang = 'ms-MY'; // Bahasa Melayu
      recognition.start();

      recognition.onresult = function(event) {
        const transcript = event.results[0][0].transcript.trim().toLowerCase();
        document.getElementById("output").innerText = "Anda kata: " + transcript;

        if (phrases[transcript]) {
          window.location.href = phrases[transcript];
        } else {
          alert("❌ Ayat tidak dikenali. Cuba lagi!");
        }
      };

      recognition.onerror = function(event) {
        alert("⚠️ Ralat pengecaman: " + event.error);
      };
    }
  </script>
</body>
</html>
