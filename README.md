

<!DOCTYPE html>

<html lang="en">

<head>

  <meta charset="UTF-8">

  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>CalmCare</title>

  <style>

    * {

      box-sizing: border-box;

    }

    body {

      margin: 0;

      min-height: 100vh;

      display: flex;

      align-items: center;

      justify-content: center;

      padding: 20px;

      font-family: Arial, sans-serif;

      background: linear-gradient(135deg, #d8f3dc, #b7e4c7);

      color: #24543b;

    }

    .card {

      width: 100%;

      max-width: 420px;

      padding: 30px 22px;

      text-align: center;

      background: white;

      border-radius: 24px;

      box-shadow: 0 10px 30px rgba(36, 84, 59, 0.12);

    }

    h1 {

      margin-top: 0;

      font-size: 32px;

    }

    h2 {

      font-size: 23px;

    }

    p {

      line-height: 1.7;

      color: #567363;

    }

    .moods {

      display: flex;

      justify-content: center;

      flex-wrap: wrap;

      gap: 8px;

      margin: 22px 0;

    }

    .moods button {

      padding: 12px;

      border: 1px solid #cce3d2;

      border-radius: 14px;

      background: #f4fbf5;

      color: #24543b;

      font-size: 14px;

    }

    .moods button.selected {

      background: #b7e4c7;

      border-color: #40916c;

    }

    .calm-button {

      width: 100%;

      padding: 15px;

      border: none;

      border-radius: 14px;

      background: #40916c;

      color: white;

      font-size: 17px;

      font-weight: bold;

    }

    #message {

      margin-top: 20px;

      font-weight: bold;

    }

    footer {

      margin-top: 25px;

      font-size: 12px;

      color: #789181;

    }

  </style>

</head>

<body>

  <main class="card">

    <h1>CalmCare 🌿</h1>

    <h2>Take a moment for yourself</h2>

    <p>You deserve peace, kindness, and a little time to breathe.</p>

    <h3>How are you feeling today?</h3>

    <div class="moods">

      <button type="button" onclick="chooseMood('Happy', this)">😊 Happy</button>

      <button type="button" onclick="chooseMood('Sad', this)">💙 Sad</button>

      <button type="button" onclick="chooseMood('Anxious', this)">🌧️ Anxious</button>

    </div>

    <button class="calm-button" type="button" onclick="findCalm()">

      Find Calm 💚

    </button>

    <p id="message" aria-live="polite">

      You are not alone. Take one gentle breath.

    </p>

    <footer>Made with care 💚 CalmCare</footer>

  </main>

  <script>

    let selectedMood = "";

    function chooseMood(mood, button) {

      selectedMood = mood;

      document.querySelectorAll(".moods button").forEach(function(item) {

        item.classList.remove("selected");

      });

      button.classList.add("selected");

      document.getElementById("message").textContent =

        "Thank you for sharing. It is okay to feel " + mood.toLowerCase() + ". 💚";

    }

    function findCalm() {

      let message = "Breathe in slowly. Breathe out gently. You are doing your best. 💚";

      if (selectedMood === "Sad") {

        message = "Be gentle with yourself. You deserve love and care. 💚";

      } else if (selectedMood === "Anxious") {

        message = "Relax your shoulders. Breathe slowly. Take one moment at a time. 🌿";

      } else if (selectedMood === "Happy") {

        message = "Enjoy this happy moment. You deserve to feel good. 🌸";

      }

      document.getElementById("message").textContent = message;

    }

  </script>

</body>

</html>
