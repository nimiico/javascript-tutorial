# ADVANCED-DOM-BANKISTmessage.parentElement.removeChild(message);

## Select, Create and Remove elements

### Select Element

- document.querySelectorAll('.section');
- document.getElementsByTagName('button');
- document.getElementsByClassName('btn')
- document.getElementById('section--1');

### Create Element

- const message = document.createElement('div'); # create an element
- message.classList.add('cookie-message'); # add it to classlist
- message.innerHTML = 'We use cookied for improved functionality and analytics. <button class="btn btn--close-cookie">Got it!</button>'; # add text contemt and button to it by write html code in it.
- header.prepend(message); # put it as first child of header (in this level you can see it in browser)
- header.append(message); # put it as last child of header (in this level you can see it in browser)
- header.before(message); # add it before the header element
- header.after(message); # add it after the header element

### Remove Element

- message.remove(); # remove element
- message.parentElement.removeChild(message); # remove by accessing to parents

## Styles, Attributes and classes

### Styles

- message.style.backgroundColor = '#37383d'; # we can change styles that we have declare them in css file by this way
- message.style.height = Number.parseFloat(getComputedStyle(message).height, 10) + 30 + 'px'; # if you didn't declare the property in css, at first we should compute it by getComputedStyle(), then change it.

### Attributes

- attributes is class, id, src, href, ... in html
- const link = document.querySelector('.nav__link--btn');
- link.getAttribute('href')= #; # get href attributes content

## Classes

- logo.classList.add('c', 'j');
- logo.classList.remove('c', 'j');
- logo.classList.toggle('c'); # if exist remove, if do not exist add
- logo.classList.contains('c');

// Don't use
- logo.clasName = 'jonas'; # override on all of class name

## Project

- btnsOpenModal.forEach(btn => btn.addEventListener('click', openModal)) # we can also use foreach for node lists (for example here is 2 button)

- e.target.getBoundingClientRect() # x and y from view port
- window.pageXOffset, window.pageYOffset # x and y from top and left of view port to x and y of web page
- document.documentElement.clientHeight, document.documentElement.clientWidth # viewport height and width

### Scrolling

- const s1coords = section1.getBoundingClientRect();
- window.scrollTo({ 					# old version of scrolling
    left: s1coords.left + window.pageXOffset,
    top: s1coords.top + window.pageYOffset,
    behavior: 'smooth',
  });

- section1.scrollIntoView({ behavior: 'smooth' }); # new version

## Events

- const alertH1 = function (e) {
    alert('addEventListener: Great! You are reading the heading :D');
     h1.removeEventListener('mouseenter', alertH1) # we can remove event. in this example event just works once and then removed.
  };
- h1.addEventListener('mouseenter', alertH1);

## Page Navigation

- document.querySelector('.nav__links').addEventListener('click', function (e) { # we can add event for parent element(.nav__links) to contain all children instead of use foreach for each children
    e.preventDefault();

    // Matching strategy
    if (e.target.classList.contains('nav__link')) { # if statement is for check we only click on somewhere has link not all of parent enviroment
      const id = e.target.getAttribute('href');     # e.target is element that click on it
      document.querySelector(id).scrollIntoView({ behavior: 'smooth' });
    }
  });

## DOM Traversing

### Going downwards: child
- const h1 = document.querySelector('h1');
- h1.querySelectorAll('.highlight'); # select all children of h1 that classnames are highlight
- h1.childNodes; # all nodes include text,... and not just elements
- h1.children; # include all elements
- h1.firstElementChild.style.color = 'white';
- h1.lastElementChild.style.color = 'orangered';

### Going upwards: parents

- h1.parentElement; # parent element
- h1.closest('.header').style.background = 'var(--gradient-secondary)'; # closest header to h1
- h1.closest('h1').style.background = 'var(--gradient-primary)'; the closest h1 to h1 (itself)

### Going sideways: siblings
- h1.previousElementSibling; # previous node
- h1.nextElementSibling; # next element

## Sticky Nav

- const header = document.querySelector('.header');
- const navHeight = nav.getBoundingClientRect().height;

- const stickyNav = function (entries) { # get 2 args: entries and observer
    const [entry] = entries; # get entry[0]
    // console.log(entry);

    if (!entry.isIntersecting) nav.classList.add('sticky'); # if 0% entry[0] is visible so intersecting be false (out 0f entry[0] viewport)
    else nav.classList.remove('sticky');
  };

- const headerObserver = new IntersectionObserver(stickyNav, { 		# IntersectionObserver (function of observing , optionObj) # when optionObj proprties happen funcion will be call
    root: null,					# intersecting is true when the properties get true
    threshold: 0, 				# when 0% of the viewport is visible
    rootMargin: `-${navHeight}px`,
  });
- headerObserver.observe(header); # we active sticky nav bu observe method to observing web page

## Reveal sections (moving elements)

- const allSections = document.querySelectorAll('.section');

- const revealSection = function (entries, observer) {
    const [entry] = entries;

    if (!entry.isIntersecting) return;

    entry.target.classList.remove('section--hidden'); # remove each target that we see 0.15 of them
    observer.unobserve(entry.target); # observe each target just once
  };

- const sectionObserver = new IntersectionObserver(revealSection, {
    root: null,
    threshold: 0.15,
  });

- allSections.forEach(function (section) { # loop for eacg section
    sectionObserver.observe(section);
    section.classList.add('section--hidden');
  });

  ## Lazy loading image

- use data-src attribute in html for saving high rsolution image address
- See example in the project

## Slider

- see example in the project

- const goToSlide = function (slide) { # put slides side by side
    slides.forEach(
      (s, i) => (s.style.transform = `translateX(${100 * (i - slide)}%)`)
    );
  };

  // Next slide
- const nextSlide = function () {
    if (curSlide === maxSlide - 1) { # for last slide to comeback to first one
      curSlide = 0;
    } else {
      curSlide++; # go to next
    }

    goToSlide(curSlide);
    activateDot(curSlide);
  };

- document.addEventListener('keydown', function (e) { # go left or right by arrowkey
    if (e.key === 'ArrowLeft') prevSlide();
    e.key === 'ArrowRight' && nextSlide();
  });

## Lifestyle DOM Events

- window.addEventListener('beforeunload', function (e) { # use it when user want to exit from page accientally. (example: Realy want to leave site)
    e.preventDefault();
    console.log(e);
    e.returnValue = '';
  });

 ## Load JavaScript on HTML

- inspect >> network # to see load time

- Defer    ->     modern browsers     Use at the end of head	best choice	<script defer src="script.js">
- Async    ->     modern browsers     Use at the end of head			<script async src="script.js">
- Regular  ->     all browsers        Use at the end of body			<script src="script.js">