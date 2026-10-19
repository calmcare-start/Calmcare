

<!DOCTYPE html>

<html lang="en">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>CalmCare - Your Peaceful Space</title>

<style>

* {

  box-sizing: border-box;

}

body {

  margin: 0;

  padding: 28px 16px;

  font-family: Arial, sans-serif;

  background: linear-gradient(160deg, #eff9f4, #dcefe6);

  color: #28594d;

}

.container {

  max-width: 460px;

  margin: 0 auto;

}

header {

  display: flex;

  align-items: center;

  justify-content: space-between;

  margin-bottom: 30px;

}

.logo {

  font-size: 27px;

  font-weight: bold;

}

.tagline {

  color: #65877a;

  font-size: 13px;

  margin-top: 5px;

}

.leaf {

  font-size: 38px;

}

.hero {

  background: white;

  border-radius: 28px;

  padding: 30px 22px;

  text-align: center;

  box-shadow: 0 12px 35px #bdd9cc80;

}

.hero-icon {

  font-size: 58px;

  margin: 5px 0 15px;

}

h1 {

  font-size: 30px;

  line-height: 1.3;

  margin: 10px 0;

}

.description {

  color: #6c887c;

  line-height: 1.7;

  font-size: 15px;

}

h2 {

  font-size: 20px;

  margin: 28px 0 16px;

}

.feelings {

  display: grid;

  grid-template-columns: repeat(3, 1fr);

  gap: 10px;

}

.feeling {

  border: 2px solid transparent;

  border-radius: 17px;

  padding: 15px 4px;

  background: #f0f7f2;

  color: #28594d;

  font-size: 14px;

  cursor: pointer;

}

.feeling span {

  display: block;

  font-size: 27px;

  margin-bottom: 8px;

}

.feeling.selected {

  border-color: #438f83;

  background: #e1f2e9;

}

.main-button {

  width: 100%;

  margin-top: 24px;

  padding: 17px;

  border: none;

  border-radius: 16px;

  background: #438f83;

  color: white;

  font-size: 17px;

  font-weight: bold;

  cursor: pointer;

}

#message {

  line-height: 1.8;

  color: #43816d;

  font-size: 15px;

}

footer {

  text-align: center;

  padding: 24px 8px 8px;

  color: #6c887c;

  font-size: 13px;

}

</style>

</head>

<body>

<div class="container">

  <header>

    <div>

      <div class="logo">CalmCare 🌿</div>

      <div class="tagline">Your peaceful space</div>

    </div>

    <div class="leaf">☘️</div>

  </header>

  <main class="hero">

    <div class="hero-icon">🌱</div>

    <h1>Take a moment<br>for yourself</h1>

    <p class="description">

      Breathe deeply. Relax your mind.

      You deserve a little peace today.

    </p>

    <h2>How are you feeling today?</h2>

    <div class="feelings">

      <button class="feeling"

        onclick="chooseFeeling('Happy', this)">

        <span>😊</span>Happy

      </button>

      <button class="feeling"

        onclick="chooseFeeling('Sad', this)">

        <span>🌧️</span>Sad

      </button>

      <button class="feeling"

        onclick="chooseFeeling('Anxious', this)">

        <span>💚</span>Anxious

      </button>

    </div>

    <button class="main-button" onclick="showMessage()">

      Find Calm ✨

    </button>

    <p id="message" aria-live="polite"></p>

  </main>

  <footer>

    A little peace, just for you 💚

  </footer>

</div>

<script>

let selectedFeeling = "";

function chooseFeeling(feeling, button) {

  selectedFeeling = feeling;

  document.querySelectorAll(".feeling").forEach(function(item) {

    item.classList.remove("selected");

  });

  button.classList.add("selected");

  document.getElementById("message").textContent =

    "Thank you for checking in with yourself. 💚";

}

function showMessage() {

  let message =

    "Breathe in slowly. Breathe out gently. You are doing your best. 💚";

  if (selectedFeeling === "Sad") {

    message =

      "Be gentle with yourself. You do not have to feel okay every moment. 💚";

  } else if (selectedFeeling === "Anxious") {

    message =

      "Relax your shoulders. Breathe in slowly, then breathe out gently. Take one moment at a time. 💚";

  } else if (selectedFeeling === "Happy") {

    message =

      "Enjoy this beautiful moment. Let yourself appreciate the good things around you. 💚";

  }

  document.getElementById("message").textContent = message;

}

</script>

</body>

</html>
