# Modal

- const model = document.querySelector('.model');

- modal.classList.remove('hidden') # remove class of modal element (here because of property of hidden class(dispay: none) when we remove this class the window is shown # notice: it does not have cama 
- modal.classList.add('hidden'); ## add class of modal element
- modal.classList.contains('hidden') # contain


- onst closeModal = function() {
  modal.classList.add('hidden');
  overlay.classList.add('hidden');
}
- overlay.addEventListener('click', closeModal); # also we can assign the function to const variable before and then use it in addEventListener
- document.addEventListener('keydown', function (e) { # with document access to no specific elemeny because key press is global event
    console.log(e.key);
})
