# MAPTY

- navigator.geolocation.getCurrentPosition(<function that if al things true>, <function for error>)

- the <script> access to before <scipit> declaration but <script> doesnt access tp next <script> that declare in html.
- leaflet library # for dispay map on your website
- copy from downlaod tab <link>, <script> and paste them into head of our html.
- copy 'const map = L.map('map').setView([51.505, -0.09], 13);' from overview tab and paste them in to js file. # 'map' is must be the id of element that we ant display map in it.
- const map = L.map('map').setView(coords, 13); # const map = L.map('element').setView([latitude, longitude], zoom value);

- map.on('click', function (mapEvent) { # add click event (like addEventListener)
  const { lat, lng } = mapEvent.latlng; # where we click

  L.marker([lat, lng]) # mark where we click
  .addTo(map) # added to map
  .bindPopup( # set popup properties
  L.popup({ # popup specifications
  maxWidth: 250,
  minWidth: 100,
  autoClose: false,
  closOnclick: false,
  className: 'running-popup', # set css style # name of class
  })
  )
  .setPopupContent('Workout') # set content
  .openPopup();
  });

- inputDistance.focus() # for put cursor at first on input.

- this in regular funtions point to undifined so we must to bind.
- callback functions that pass to eventlistener function, their this point to the object that attach to eventlistener

- add code to html

```
_renderWorkout(workout) {
    let html = `
      <li class="workout workout--${workout.type}" data-id="${workout.id}">
        <h2 class="workout__title">${workout.description}</h2>
        <div class="workout__details">
          <span class="workout__icon">${
            workout.type === 'running' ? '🏃‍♂️' : '🚴‍♀️'
          }</span>
          <span class="workout__value">${workout.distance}</span>
          <span class="workout__unit">km</span>
        </div>
        <div class="workout__details">
          <span class="workout__icon">⏱</span>
          <span class="workout__value">${workout.duration}</span>
          <span class="workout__unit">min</span>
        </div>
    `;

    if (workout.type === 'running')
      html += `
        <div class="workout__details">
          <span class="workout__icon">⚡️</span>
          <span class="workout__value">${workout.pace.toFixed(1)}</span>
          <span class="workout__unit">min/km</span>
        </div>
        <div class="workout__details">
          <span class="workout__icon">🦶🏼</span>
          <span class="workout__value">${workout.cadence}</span>
          <span class="workout__unit">spm</span>
        </div>
      </li>
      `;
}
```

- this.#map.setView(workout.coords, this.#mapZoomLevel, { # map.setView(locatin coords, zoomlevel, option object) # go to that coordinates
  animate: true,
  pan: {
  duration: 1,
  },
  });
- localStorage.setItem('workouts', JSON.stringify(this.#workouts)); # store in localstorge # localStorage.setItem(key, value)
- JSON.stringify(Object) # convert object to string
- Inspect >> Application >> local storage # see the table

- const data = JSON.parse(localStorage.getItem('workouts')); # get data from local storage by pass key
- JSON.parse(localStorage.getItem('workouts')) # conver string to object

- when we get objects from string that stored in local storage, now thy don't inherits methods and chain prototype is broken

- localStorage.removeItem('workouts'); # remove value of this key from local storage
- location.reload(); # reload page # locatin is a big object that has alot methods
