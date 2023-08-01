# GUESS MY NUMBER (PROJECT-1)

- DOM -> is a connection between html and javascript
- DOM created automatically by the browser as soon as html page load.
- document is special obj that is the entry point to DOM. for example: document.querySelector()

- document.querySelector('.message'); # access to element in html by class of element 
- document.querySelector('.message'); # access to element in html by id of element 
- document.querySelector('.number').textContent = 13; # set value
- document.querySelector('.number').value = 23; # set value

- document.querySelector('.check').addEventListener('click', function() { # event listener # first arg is event kind, second one is the thing that we want to do
  const guess = Number(document.querySelector('.guess').value);
  console.log(typeof guess)
});

- const number = Math.random() * 20 # get random number between 0 to 19
- const number = Math.trunc(Math.random() * 20 + 1) # get random integer number between 1 to 20

- document.querySelector('.number').style.width = '30rem'; # change style and numbers must be in ''
