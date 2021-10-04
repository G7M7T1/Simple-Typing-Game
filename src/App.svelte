<script>
  const words = [
    "Hello",
    "World",
    "Earth",
    "Developer",
    "reveal",
    "Installation",
    "Dictionary",
    "Cambridge",
    "search",
    "concerns",
    "intended",
    "approaching",
    "engaged",
    "obtained",
    "straight",
    "properties",
    "passages",
    "commission",
    "circumstances",
    "instituting",
    "campaign",
    "conferred",
    "entertaining",
    "Contracts",
    "convention",
    "financial",
    "novel",
    "compelling",
    "venture",
    "undertaken",
    "and",
    "Yes",
    "majority",
    "chamber",
    "manifest",
    "resources",
    "distinction",
    "Handling",
    "Bindings",
    "components",
    "directive",
    "uncheck",
    "attribute",
    "element",
    "instance",
    "boasting",
    "advocates",
    "notwithstand",
    "multitude",
    "substantial",
    "modified",
    "Recommend",
    "sveltejs",
    "Vanilla",
    "JavaScript",
    "warranted",
    "rider",
    "Dense",
    "ordained",
    "vexing",
    "gravity",
    "suspended",
    "conspicuous",
    "assented",
    "purse",
    "sanctioned",
    "proceeding",
    "exalt",
    "malice",
    "extravagant",
    "assailing",
    "sublimest",
    "exertion",
    "endowed",
    "humiliated",
    "suffrage",
    "Musing",
    "indications",
    "dispatched",
    "tract",
    "digestive",
    "consequence",
    "latitude",
    "controversial",
    "employees",
    "protesters",
    "undertaking",
  ];

  // init game
  let randomWord;
  let typeText;
  let score = 0;
  let time = 10;
  let overString;
  let difficultySelection;

  const timeInterval = setInterval(updateTime, 1000);

  function getRandomWord() {
    return words[Math.floor(Math.random() * words.length)];
  }
  function addWord() {
    randomWord = getRandomWord();
  }

  // update Score
  function updateScore() {
    score++;
  }

  function updateTime() {
    time--;

    if (time == 0) {
      clearInterval(timeInterval);
      gameOver();
    }
  }

  // game over here
  function gameOver() {
    overString = `<h1>Time ran out</h1>
    <p>Your final score is ${score}</p>
    <button onclick="location.reload()">Reload</button>`;

    const endgameelement = document.getElementById("end-game-container");
    endgameelement.style.display = "flex";
  }

  addWord();
</script>

<main>
  <button class="settings-btn" id="settings-btn">
    <i class="fas fa-cog" />
  </button>
  <div class="settings hide" id="settings">
    <form id="settins-form">
      <div class="diff">
        <label for="difficulty">Difficulty</label>
        <select id="difficulty">
          <option value="easy">Easy</option>
          <option value="medium">Medium</option>
          <option value="hard">Hard</option>
        </select>
      </div>
    </form>
  </div>

  <div class="container">
    <h2>Speed Typer</h2>
    <small>Type the following Word</small>
    <h1 id="word">{randomWord}</h1>
    <input
      type="text"
      id="text"
      on:input={(e) => {
        typeText = e.target.value;
        if (typeText == randomWord) {
          addWord();
          updateScore();
          e.target.value = "";
          if (difficulty == "hard") {
            time += 2;
          } else if (difficulty == "medium") {
            time += 3;
          } else {
            time += 5;
          }
        }
      }}
      autocomplete="off"
      placeholder="Type the word here..."
    />
    <p class="time-container">
      Time Left: <span id="time">{time}s</span>
    </p>

    <p class="score-container">
      Score: <span id="score">{score}</span>
    </p>
    <div class="end-game-container" id="end-game-container">
      {@html overString}
    </div>
  </div>
  <script>
    settingsBtn = document.getElementById("settings-btn");
    settings = document.getElementById("settings");
    settinsForm = document.getElementById("settins-form");
    difficultySelection = document.getElementById("difficulty").value;
    settingsBtn.addEventListener("click", () =>
      settings.classList.toggle("hide")
    );
    let difficulty = "easy";
    settinsForm.addEventListener("change", (e) => {
      difficulty = e.target.value;
      localStorage.setItem("difficulty", difficulty);
    });
    difficulty =
      localStorage.getItem("difficulty") !== null
        ? localStorage.getItem("difficulty")
        : "easy";
    difficultySelection =
      localStorage.getItem("difficulty") !== null
        ? localStorage.getItem("difficulty")
        : "easy";
    document.getElementById("difficulty").value = difficultySelection;
  </script>
</main>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Gemunu+Libre&display=swap");
  * {
    box-sizing: border-box;
  }

  :global(body) {
    background-color: #333;
    display: flex;
    align-items: center;
    color: white;
    justify-content: center;
    min-height: 100vh;
    margin: 0;
    font-family: "Gemunu Libre", sans-serif;
  }

  button {
    cursor: pointer;
    font-size: 14px;
    border-radius: 4px;
    padding: 5px 15px;
  }

  select {
    width: 200px;
    padding: 5px;
    appearance: none;
    -webkit-appearance: none;
    -moz-appearance: none;
    border-radius: 0;
    background-color: white;
  }

  select:focus,
  button:focus {
    outline: 0;
  }

  .settings-btn {
    position: absolute;
    bottom: 30px;
    left: 30px;
  }

  .settings {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    color: white;
    background-color: rgba(0, 0, 0, 0.2);
    height: 70px;
    display: flex;
    align-items: center;
    justify-content: center;
    transform: translateY(0);
    transition: transform 0.3s ease-in-out;
    text-align: center;
  }

  .settings.hide {
    transform: translateY(-100%);
  }

  .container {
    background-color: rgba(0, 0, 0, 0.3);
    padding: 20px;
    border-radius: 1rem;
    box-shadow: 0 3px 10px black;
    color: #fff;
    position: relative;
    text-align: center;
    width: 550px;
  }

  .container h2 {
    background-color: rgba(0, 0, 0, 0.3);
    padding: 8px;
    border-radius: 0.5rem;
    margin: 0 0 40px;
  }

  h1 {
    margin: 0;
  }

  input {
    border: 0;
    border-radius: 0.5rem;
    font-size: 2rem;
    width: 300px;
    padding: 12px 20px;
    margin-top: 10px;
  }

  .score-container {
    position: absolute;
    top: 60px;
    right: 20px;
  }

  .time-container {
    position: absolute;
    top: 60px;
    left: 20px;
  }

  .end-game-container {
    background-color: #282626;
    display: none;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 1;
  }
</style>
