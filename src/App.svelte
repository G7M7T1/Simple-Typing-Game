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
  ];

  // init game
  let randomWord;
  let typeText = "";
  let score = 0;
  let time = 10;

  function getRandomWord() {
    return words[Math.floor(Math.random() * words.length)];
  }
  randomWord = getRandomWord();
  console.log(typeText);
</script>

<main>
  <button class="settings-btn" id="settings-btn">
    <i class="fas fa-cog" />
  </button>
  <div class="settings" id="settings">
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
      autocomplete="off"
      placeholder="Type the word here..."
    />
    <p class="time-container">
      Time Left: <span id="time">10s</span>
    </p>

    <p class="score-container">
      Score: <span id="score">0</span>
    </p>
    <div class="end-game-container" id="end-game-container" />
  </div>
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
    background-color: inherit;
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
