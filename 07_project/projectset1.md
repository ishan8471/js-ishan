# Project related to DOM

## Project links
[click here](https://stackblitz.com/edit/dom-project-chaiaurcode?file=index.html)

# Solution code

## Project 1 solution


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
