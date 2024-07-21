# Rock Paper Scissors Game

## Introduction

Welcome to the Rock-Paper-Scissors game project! This is a fun and interactive web-based game where you can play the classic Rock-Paper-Scissors game against the computer. The game keeps track of the score and announces the winner of each round.

## Features

- **Interactive Gameplay**: Play Rock-Paper-Scissors against the computer.
- **Score Tracking**: Keeps track of both the user and computer scores.
- **Winner Announcement**: Announces the winner of each round.
- **Responsive Design**: Optimized for various screen sizes.

## Technologies Used

- **HTML**: For structuring the content.
- **CSS**: For styling the game.
- **JavaScript**: For game logic and interactivity.

## Installation

To run this project locally, follow these steps:

1. **Clone the repository**:
    ```bash
    git clone https://github.com/your-username/rock-paper-scissors.git
    ```
2. **Navigate to the project directory**:
    ```bash
    cd rock-paper-scissors
    ```
3. **Open `index.html` in your favorite browser**.

## Usage

- Click on any of the Rock, Paper, or Scissors choices to make your move.
- The computer will randomly select its move.
- The result of the round will be displayed along with the updated scores.
- Keep playing to see who reaches the highest score!

## Code Overview

### HTML

The HTML file structures the game layout, including the choice buttons and score display.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Rock Paper Scissors Game</title>
    <link rel="stylesheet" href="style.css" />
</head>
<body>
    <h1>Rock Paper Scissors</h1>
    <div class="choices">
        <div class="choice" id="rock">
            <img src="./images/rock.png" />
        </div>
        <div class="choice" id="paper">
            <img src="./images/paper.png" />
        </div>
        <div class="choice" id="scissors">
            <img src="./images/scissors.png" />
        </div>
    </div>
    <div class="score-board">
        <div class="score">
            <p id="user-score">0</p>
            <p>You</p>
        </div>
        <div class="score">
            <p id="comp-score">0</p>
            <p>Comp</p>
        </div>
    </div>
    <div class="msg-container">
        <p id="msg">Play your move</p>
    </div>
    <script src="app.js"></script>
</body>
</html>
```

### CSS

The CSS file styles the game, making it visually appealing.

```css
* {
  margin: 0;
  padding: 0;
  text-align: center;
}

h1 {
  background-color: #081b31;
  color: #fff;
  height: 5rem;
  line-height: 5rem;
}

.choice {
  height: 165px;
  width: 165px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.choice:hover {
  cursor: pointer;
  background-color: #081b31;
}

img {
  height: 150px;
  width: 150px;
  object-fit: cover;
  border-radius: 50%;
}

.choices {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 3rem;
  margin-top: 5rem;
}

.score-board {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 2rem;
  margin-top: 3rem;
  gap: 5rem;
}

#user-score,
#comp-score {
  font-size: 4rem;
}

.msg-container {
  margin-top: 5rem;
}

#msg {
  background-color: #081b31;
  color: #fff;
  font-size: 2rem;
  display: inline;
  padding: 1rem;
  border-radius: 1rem;
}
```

### JavaScript

The JavaScript file handles the game logic, including user choices, computer choices, and winner detection.

```javascript
let userScore = 0;
let compScore = 0;

const choices = document.querySelectorAll(".choice");
const msg = document.querySelector("#msg");

const userScorePara = document.querySelector("#user-score");
const compScorePara = document.querySelector("#comp-score");

const genCompChoice = () => {
  const options = ["rock", "paper", "scissors"];
  const randIdx = Math.floor(Math.random() * 3);
  return options[randIdx];
};

const drawGame = () => {
  msg.innerText = "Game was Draw. Play again.";
  msg.style.backgroundColor = "#081b31";
};

const showWinner = (userWin, userChoice, compChoice) => {
  if (userWin) {
    userScore++;
    userScorePara.innerText = userScore;
    msg.innerText = `You win! Your ${userChoice} beats ${compChoice}`;
    msg.style.backgroundColor = "green";
  } else {
    compScore++;
    compScorePara.innerText = compScore;
    msg.innerText = `You lost. ${compChoice} beats your ${userChoice}`;
    msg.style.backgroundColor = "red";
  }
};

const playGame = (userChoice) => {
  const compChoice = genCompChoice();

  if (userChoice === compChoice) {
    drawGame();
  } else {
    let userWin = true;
    if (userChoice === "rock") {
      userWin = compChoice === "paper" ? false : true;
    } else if (userChoice === "paper") {
      userWin = compChoice === "scissors" ? false : true;
    } else {
      userWin = compChoice === "rock" ? false : true;
    }
    showWinner(userWin, userChoice, compChoice);
  }
};

choices.forEach((choice) => {
  choice.addEventListener("click", () => {
    const userChoice = choice.getAttribute("id");
    playGame(userChoice);
  });
});
```

## Contribution

Feel free to fork this project, submit issues, and pull requests. Contributions are always welcome!
