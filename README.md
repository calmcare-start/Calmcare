


<!DOCTYPE html>

<html lang="en">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1">

<title>CalmCare</title>

<style>

body {

  margin: 0;

  padding: 24px;

  font-family: Arial, sans-serif;

  background: #edf7f0;

  color: #245440;

  text-align: center;

}

main {

  max-width: 500px;

  margin: auto;

}

section {

  background: white;

  padding: 24px;

  margin: 18px 0;

  border-radius: 22px;

  box-shadow: 0 4px 15px #0000000d;

}

h1 { color: #287451; }

button {

  background: #347c59;

  color: white;

  border: 0;

  border-radius: 12px;

  padding: 13px 20px;

  font-size: 16px;

  margin: 6px;

}

textarea, select {

  box-sizing: border-box;

  width: 100%;

  padding: 12px;

  border: 1px solid #c9dfd0;

  border-radius: 10px;

  margin: 8px 0;

  font-size: 16px;

}

#circle {

  width: 110px;

  height: 110px;

  margin: 25px auto;

  border-radius: 50%;

  background: #a8d9b9;

  display: grid;

  place-items: center;

  transition: transform 4s;

}

</style>

</head>

<body>

<main>

<h1>🌿 CalmCare</h1>

<p>A little calm, one breath at a time.</p>

<section>

<h2>Your moment of peace</h2>

<p id="message">Take a gentle breath.</p>

<div id="circle">💚</div>

<button onclick="breathe()">Find Calm</button>

<button onclick="stopBreathing()">Stop</button>

</section>

<section>

<h2>🌙 Sleep Check-in</h2>

<select id="sleep">

<option value="">How did you sleep?</option>

<option>Less than 4 hours</option>

<option>4–5 hours</option>

<option>6–7 hours</option>

<option>8 or more hours</option>

</select>

<button onclick="saveSleep()">Save Sleep</button>

<p id="sleepResult"></p>

</section>

<section>

<h2>💚 Kind Thoughts</h2>

<textarea id="note" rows="4"

placeholder="Write a kind thought for yourself..."></textarea>

<button onclick="saveNote()">Save Note</button>

<p id="noteResult"></p>

</section>

</main>

<script>

let timer;

let running = false;

function breathe() {

  if (running) return;

  running = true;

  let inhale = true;

  function cycle() {

    if (!running) return;

    document.getElementById("message").textContent =

      inhale ? "Breathe in slowly..." : "Breathe out gently...";

    document.getElementById("circle").style.transform =

      inhale ? "scale(1.3)" : "scale(0.85)";

    inhale = !inhale;

    timer = setTimeout(cycle, inhale ? 4000 : 6000);

  }

  cycle();

}

function stopBreathing() {

  running = false;

  clearTimeout(timer);

  document.getElementById("circle").style.transform = "scale(1)";

  document.getElementById("message").textContent =

    "Take a gentle breath. 💚";

}

function saveSleep() {

  const value = document.getElementById("sleep").value;

  if (!value) {

    document.getElementById("sleepResult").textContent =

      "Please choose an answer.";

    return;

  }

  try { localStorage.setItem("calmcare-sleep", value); } catch(e) {}

  document.getElementById("sleepResult").textContent =

    "Your sleep check-in is saved. 💚";

}

function saveNote() {

  const value = document.getElementById("note").value.trim();

  if (!value) {

    document.getElementById("noteResult").textContent =

      "Write a kind thought first.";

    return;

  }

  try { localStorage.setItem("calmcare-note", value); } catch(e) {}

  document.getElementById("noteResult").textContent =

    "Your kind thought is saved. 🌿";

}

try {

  document.getElementById("note").value =

    localStorage.getItem("calmcare-note") || "";

  if (localStorage.getItem("calmcare-sleep")) {

    document.getElementById("sleepResult").textContent =

      "Previous check-in: " + localStorage.getItem("calmcare-sleep");

  }

} catch(e) {}

</script>

</body>

</html>DOCTYPE html>

<html lang="en">

<head>

  <meta charset="UTF-8">

  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>CalmCare</title>

  <style>
0
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


<!DOCTYPE html>

<html lang="en">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1">

<title>CalmCare</title>

<style>

body {

  margin: 0;

  padding: 24px;

  font-family: Arial, sans-serif;

  background: #edf7f0;

  color: #245440;

  text-align: center;

}

main {

  max-width: 500px;

  margin: auto;

}

section {

  background: white;

  padding: 24px;

  margin: 18px 0;

  border-radius: 22px;

  box-shadow: 0 4px 15px #0000000d;

}

h1 { color: #287451; }

button {

  background: #347c59;

  color: white;

  border: 0;

  border-radius: 12px;

  padding: 13px 20px;

  font-size: 16px;

  margin: 6px;

}

textarea, select {

  box-sizing: border-box;

  width: 100%;

  padding: 12px;

  border: 1px solid #c9dfd0;

  border-radius: 10px;

  margin: 8px 0;

  font-size: 16px;

}

#circle {

  width: 110px;

  height: 110px;

  margin: 25px auto;

  border-radius: 50%;

  background: #a8d9b9;

  display: grid;

  place-items: center;

  transition: transform 4s;

}

</style>

</head>

<body>

<main>

<h1>🌿 CalmCare</h1>

<p>A little calm, one breath at a time.</p>

<section>

<h2>Your moment of peace</h2>

<p id="message">Take a gentle breath.</p>

<div id="circle">💚</div>

<button onclick="breathe()">Find Calm</button>

<button onclick="stopBreathing()">Stop</button>

</section>

<section>

<h2>🌙 Sleep Check-in</h2>

<select id="sleep">

<option value="">How did you sleep?</option>

<option>Less than 4 hours</option>

<option>4–5 hours</option>

<option>6–7 hours</option>

<option>8 or more hours</option>

</select>

<button onclick="saveSleep()">Save Sleep</button>

<p id="sleepResult"></p>

</section>

<section>

<h2>💚 Kind Thoughts</h2>

<textarea id="note" rows="4"

placeholder="Write a kind thought for yourself..."></textarea>

<button onclick="saveNote()">Save Note</button>

<p id="noteResult"></p>

</section>

</main>

<script>

let timer;

let running = false;

function breathe() {

  if (running) return;

  running = true;

  let inhale = true;

  function cycle() {

    if (!running) return;

    document.getElementById("message").textContent =

      inhale ? "Breathe in slowly..." : "Breathe out gently...";

    document.getElementById("circle").style.transform =

      inhale ? "scale(1.3)" : "scale(0.85)";

    inhale = !inhale;

    timer = setTimeout(cycle, inhale ? 4000 : 6000);

  }

  cycle();

}

function stopBreathing() {

  running = false;

  clearTimeout(timer);

  document.getElementById("circle").style.transform = "scale(1)";

  document.getElementById("message").textContent =

    "Take a gentle breath. 💚";

}

function saveSleep() {

  const value = document.getElementById("sleep").value;

  if (!value) {

    document.getElementById("sleepResult").textContent =

      "Please choose an answer.";

    return;

  }

  try { localStorage.setItem("calmcare-sleep", value); } catch(e) {}

  document.getElementById("sleepResult").textContent =

    "Your sleep check-in is saved. 💚";

}

function saveNote() {

  const value = document.getElementById("note").value.trim();

  if (!value) {

    document.getElementById("noteResult").textContent =

      "Write a kind thought first.";

    return;

  }

  try { localStorage.setItem("calmcare-note", value); } catch(e) {}

  document.getElementById("noteResult").textContent =

    "Your kind thought is saved. 🌿";

}

try {

  document.getElementById("note").value =

    localStorage.getItem("calmcare-note") || "";

  if (localStorage.getItem("calmcare-sleep")) {

    document.getElementById("sleepResult").textContent =

      "Previous check-in: " + localStorage.getItem("calmcare-sleep");

  }

} catch(e) {}

</script>

</body>

</html>




<!DOCTYPE html>

<html lang="en">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1">

<title>CalmCare</title>

<style>

body {

  margin: 0;

  padding: 24px;

  font-family: Arial, sans-serif;

  background: #edf7f0;

  color: #245440;

  text-align: center;

}

main {

  max-width: 500px;

  margin: auto;

}

section {

  background: white;

  padding: 24px;

  margin: 18px 0;

  border-radius: 22px;

  box-shadow: 0 4px 15px #0000000d;

}

h1 { color: #287451; }

button {

  background: #347c59;

  color: white;

  border: 0;

  border-radius: 12px;

  padding: 13px 20px;

  font-size: 16px;

  margin: 6px;

}

textarea, select {

  box-sizing: border-box;

  width: 100%;

  padding: 12px;

  border: 1px solid #c9dfd0;

  border-radius: 10px;

  margin: 8px 0;

  font-size: 16px;

}

#circle {

  width: 110px;

  height: 110px;

  margin: 25px auto;

  border-radius: 50%;

  background: #a8d9b9;

  display: grid;

  place-items: center;

  transition: transform 4s;

}

</style>

</head>

<body>

<main>

<h1>🌿 CalmCare</h1>

<p>A little calm, one breath at a time.</p>

<section>

<h2>Your moment of peace</h2>

<p id="message">Take a gentle breath.</p>

<div id="circle">💚</div>

<button onclick="breathe()">Find Calm</button>

<button onclick="stopBreathing()">Stop</button>

</section>

<section>

<h2>🌙 Sleep Check-in</h2>

<select id="sleep">

<option value="">How did you sleep?</option>

<option>Less than 4 hours</option>

<option>4–5 hours</option>

<option>6–7 hours</option>

<option>8 or more hours</option>

</select>

<button onclick="saveSleep()">Save Sleep</button>

<p id="sleepResult"></p>

</section>

<section>

<h2>💚 Kind Thoughts</h2>

<textarea id="note" rows="4"

placeholder="Write a kind thought for yourself..."></textarea>

<button onclick="saveNote()">Save Note</button>

<p id="noteResult"></p>

</section>

</main>

<script>

let timer;

let running = false;

function breathe() {

  if (running) return;

  running = true;

  let inhale = true;

  function cycle() {

    if (!running) return;

    document.getElementById("message").textContent =

      inhale ? "Breathe in slowly..." : "Breathe out gently...";

    document.getElementById("circle").style.transform =

      inhale ? "scale(1.3)" : "scale(0.85)";

    inhale = !inhale;

    timer = setTimeout(cycle, inhale ? 4000 : 6000);

  }

  cycle();

}

function stopBreathing() {

  running = false;

  clearTimeout(timer);

  document.getElementById("circle").style.transform = "scale(1)";

  document.getElementById("message").textContent =

    "Take a gentle breath. 💚";

}

function saveSleep() {

  const value = document.getElementById("sleep").value;

  if (!value) {

    document.getElementById("sleepResult").textContent =

      "Please choose an answer.";

    return;

  }

  try { localStorage.setItem("calmcare-sleep", value); } catch(e) {}

  document.getElementById("sleepResult").textContent =

    "Your sleep check-in is saved. 💚";

}

function saveNote() {

  const value = document.getElementById("note").value.trim();

  if (!value) {

    document.getElementById("noteResult").textContent =

      "Write a kind thought first.";

    return;

  }

  try { localStorage.setItem("calmcare-note", value); } catch(e) {}

  document.getElementById("noteResult").textContent =

    "Your kind thought is saved. 🌿";

}

try {

  document.getElementById("note").value =

    localStorage.getItem("calmcare-note") || "";

  if (localStorage.getItem("calmcare-sleep")) {

    document.getElementById("sleepResult").textContent =

      "Previous check-in: " + localStorage.getItem("calmcare-sleep");

  }

} catch(e) {}

</script>

</body>

</html>

