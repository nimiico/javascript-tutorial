# ASYNCHRONOUS

- in javascript codes execute in callstack and asynchronous codes like feth, load iamge, timers, ... go to web api, then fetch codes go to microtasks qeue and when call atack is empty they go there and it will be executed, also load image go to callback qeue and then when callstack is empty go there and executed. microtasks have priority than callback

- AJAX -> Allows us to comminucate with remote web servers in asynchronous way
- API -> pease of software that can be used by another peace of software, in order to allow applications to talk to each other.

- online API -> application running on a server that receives requests for data, and sends data back as response (API conventional)

## XML Request

- see apis # search on github -> public apis

1. const request = new XMLHttpRequest(); # create object
2. request.open('GET', '`https://restcountries.eu/rest/v2/name/iran`') # request.open(request type, url)
3. request.send(); # send request
4. request.addEventListener('load', function () {
   const [data] = JSON.parse(this.responseText); # load data and convert string to object
   console.log(data);
   })

## Promises

1. pending -> a continer that before future value
2. settled:

- fulfuild -> success! the value is available now
- rejected -> has an error

- in 400's errors not, the fetch promise does not reject so we throw error manually

- const getCountryData = function (country) {
  fetch(`https://restcountries.eu/rest/v2/name/${country}`) # at first fetch data to promise
  .then(function (response) { # then method pass value of function to next function, so here we convert promise to json to be readable
  console.log(response);
  return response.json();
  })
  .then(function (data) { # here get json form of data an show it
  console.log(data);
  renderCountry(data[0]);
  }); # we can add another then and get response like before
  .catch(err => { # catch error
  console.error(`${err} 💥💥💥`);
  renderError(`Something went wrong 💥💥 ${err.message}. Try again!`);
  })
  .finally(() => { # always run
  countriesContainer.style.opacity = 1;
  });
  };
- const getCountryData = function (country) {
  // Country 1
  fetch(`https://restcountries.eu/rest/v2/name/${country}`)
  .then(response => {
  console.log(response);

       if (!response.ok)	# for 400 errors is false
         throw new Error(`Country not found (${response.status})`);

       return response.json();

  })
  };

  ## Async

- it's like promiises behind the scenes

- const whereAmI = async function () { # get function to asynchronous
  try { # use try / catch block for handling errors
  // Geolocation
  const pos = await getPosition(); # it's like then method
  const { latitude: lat, longitude: lng } = pos.coords;

      // Reverse geocoding
      const resGeo = await fetch(`https://geocode.xyz/${lat},${lng}?geoit=json`);
      if (!resGeo.ok) throw new Error('Problem getting location data');

      const dataGeo = await resGeo.json();
      console.log(dataGeo);

      // Country data
      const res = await fetch(
        `https://restcountries.eu/rest/v2/name/${dataGeo.country}`
      );

      if (!res.ok) throw new Error('Problem getting country');

      const data = await res.json();
      console.log(data);
      renderCountry(data[0]);

  } catch (err) {
  console.error(`${err} 💥`);
  renderError(`💥 ${err.message}`);

      // Reject promise returned from async function
      throw err;

  }
  };

- (async function () # for see returning value of async function, we should to put it to another async function
  try {
  const city = await whereAmI(); # return value of whereamI
  console.log(`2: ${city}`);
  } catch (err) { # if whereamI has error, we also should again throw err in cath block of whereamI to give it here (because we handle errors of try block by catch block and so for see the error of that we must to throw error)
  console.error(`2: ${err.message} 💥`);
  }
  console.log('3: Finished getting location');
  )(); # call it ()

- above code is for returning value of whereamI async function

- Promis.resolve()
- Promise.reject()

## Parallel

### Promise.all

- const get3Countries = async function (c1, c2, c3) {
  try {

      const data = await Promise.all([ # fetch data at the same time and put it in an array
        getJSON(`https://restcountries.eu/rest/v2/name/${c1}`),
        getJSON(`https://restcountries.eu/rest/v2/name/${c2}`),
        getJSON(`https://restcountries.eu/rest/v2/name/${c3}`),
      ]);
      console.log(data.map(d => d[0].capital));

  } catch (err) {
  console.error(err);
  }
  };

- get3Countries('portugal', 'canada', 'tanzania');

### Promise.race

- const timeout = function (sec) {
  return new Promise(function (\_, reject) {
  setTimeout(function () {
  reject(new Error('Request took too long!'));
  }, sec \* 1000);
  });
  };

- Promise.race([
  getJSON(`https://restcountries.eu/rest/v2/name/tanzania`), # just give one object not array, so if we success give us the faster one, if one of them reject we get an error.
  timeout(5), # set 5 sec to resolve data, if take more time, get error
  ])
  .then(res => console.log(res[0]))
  .catch(err => console.error(err));

### Promise.allsetlled

- Promise.allSettled([ # give us an array, shoe resolve and rejected data
  Promise.resolve('Success'),
  Promise.reject('ERROR'),
  Promise.resolve('Another success'),
  ]).then(res => console.log(res));

### Promise.any

- it's similar to race, so return the first fulfilled, but ignore any reject
