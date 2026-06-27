# Project related to DOM

## Project links
[click here](https://stackblitz.com/edit/dom-project-chaiaurcode?file=index.html)

# Solution code

## Project 1 solution code


```javascript
console.log("Ishan");
const buttons = document.querySelectorAll('.button');
// console.log(buttons);
const boddy = document.querySelector('body');
// console.log(boddy)

buttons.forEach(function (button) {
  console.log(button);
  button.addEventListener('click', function (e) {
    console.log(e);
    console.log(e.target);
    if (e.target.id === 'grey') {
      boddy.style.backgroundColor = e.target.id;
    }
    if (e.target.id === 'white') {
      boddy.style.backgroundColor = e.target.id;
    }
    if (e.target.id === 'blue') {
      boddy.style.backgroundColor = e.target.id;
    }
    if (e.target.id === 'yellow') {
      boddy.style.backgroundColor = e.target.id;
    }
    // if (e.target.id === 'purple') {
    //   boddy.style.backgroundColor = e.target.id;
    // }
  });
});


```

## Project 2 solution code

```javascript
const form = document.querySelector('form');

// this usecase will give you empty value
// const height = parseInt(document.querySelector('#height').value);

form.addEventListener('submit', function (e) {
  e.preventDefault();

  const height = parseInt(document.querySelector('#height').value);
  const weight = parseInt(document.querySelector('#weight').value);
  const results = document.querySelector('#results');

  if (height === '' || height < 0 || isNaN(height)) {
    results.innerHTML = `Please Enter a Valid Height ${height}`;
  } else if (weight === '' || weight < 0 || isNaN(weight)) {
    results.innerHTML = `Please Enter a Valid Weight ${weight}`;
  } else {
    const bmi = ((weight / (height * height)) * 10000).toFixed(2);
    results.innerHTML = `<span> ${bmi} </span>`;
    // if (bmi < 18.6) {
    //   results.innerHTML = `<span> ${bmi} <br> Under Weight </span>`;
    // } else if (bmi >= 18.6 && bmi < 24.9) {
    //   results.innerHTML = `<span> ${bmi} <br> Normal Range </span>`;
    // } else {
    //   results.innerHTML = `<span> ${bmi} <br> Over Weight  </span>`;
    // }
  }
});

```

## Project 3 solution code

```javascript

const clock = document.getElementById('clock');

// const clock = document.querySelector('#clock')

// let date = new Date();
// clock.innerHTML = date.toLocaleTimeString();

setInterval(function () {
  let date = new Date();
  // console.log(date.toLocaleTimeString());
  clock.innerHTML = date.toLocaleTimeString();
}, 1000);
```

## Project 4 solution code

```javascript
// console.log(parseInt(Math.random() * 100 + 1));

let randomNumber = parseInt(Math.random() * 100 + 1);

const submit = document.querySelector('#subt');
const userInput = document.querySelector('#guessField');
const guesslot = document.querySelector('.guesses');
const remaining = document.querySelector('.lastResult');
const lowOrHi = document.querySelector('.lowOrHi');
const startOver = document.querySelector('.resultParas');

const p = document.createElement('p');

let prevGuess = [];
let numGuess = 1;

let playGame = true;

if (playGame) {
  submit.addEventListener('click', function (e) {
    e.preventDefault();
    const guess = parseInt(userInput.value);
    console.log(guess);
    validateGuess(guess);
  });
}

function validateGuess(guess) {
  if (isNaN(guess)) {
    alert('Plaease enter a valid Number');
  } else if (guess < 1) {
    alert('Plaease enter a greater Number');
  } else if (guess > 100) {
    alert('Plaease enter a smaller Number');
  } else {
    prevGuess.push(guess);
    if (numGuess === 10) {
      displayGuess(guess);
      displayMessage(`Game Over. Random number was ${randomNumber}`);
      endGame();
    } else {
      displayGuess(guess);
      checkGuess(guess);
    }
  }
}
function checkGuess(guess) {
  if (guess === randomNumber) {
    displayMessage(`You guessed it right`);
    endGame();
  } else if (guess < randomNumber) {
    displayMessage(`Number is too LOW`);
  } else if (guess > randomNumber) {
    displayMessage(`Number is too HIGH`);
  }
}
function displayGuess(guess) {
  // cleanup method
  userInput.value = '';
  guesslot.innerHTML += `${guess} `;
  numGuess++;
  remaining.innerHTML = `${11 - numGuess}`;
}
function displayMessage(message) {
  lowOrHi.innerHTML = `<h2>${message}</h2>`;
}
function endGame() {
  userInput.value = '';
  userInput.setAttribute('disabled', '');
  p.classList.add('button');
  p.innerHTML = `<h2 id="newGame">Start New Game</h2>`;
  startOver.appendChild(p);
  playGame = false;
  newGame();
}
function newGame() {
  const newgamebutton = document.querySelector('#newGame');
  newgamebutton.addEventListener('click', function (e) {
    displayMessage(``);
    randomNumber = parseInt(Math.random() * 100 + 1);
    prevGuess = [];
    numGuess = 1;
    guesslot.innerHTML = '';
    remaining.innerHTML = `${11 - numGuess}`;
    userInput.removeAttribute('disabled');
    startOver.removeChild(p);
    playGame = true;
  });
}
```