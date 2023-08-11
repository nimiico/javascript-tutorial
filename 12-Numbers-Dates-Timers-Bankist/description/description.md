# NUMBERS-DATES-TIMERS-BANKIST

## Convert and Checking number

- Number('23'); ~ +'23' # convert to number

- Number.parseInt('30px', 10) = 30 # convert to number
- Number.parseInt('  2.5rem  ') = 2
- Number.parseFloat('  2.5rem  ') = 2.5

- Number.isFinite(23 / 0) = false # number checking
- Number.isInteger(23) = true # integer checking

## Math

- console.log(Math.max(5, 18, '23px', 11, 2)); # 23
- console.log(Math.floor(Math.random() * 6) + 1); # 1 to 6
- console.log(Math.round(23.9)); # 24 # nearest number
- console.log(Math.ceil(23.3)); # 24 # upper number
- console.log(Math.floor(23.3)); # 23
- console.log(Math.floor(-23.3)); # -24

- console.log((2.7).toFixed(0)); # 3 # also returns string
- console.log((2.7).toFixed(3)); # 2.700
- console.log((2.345).toFixed(2)); # 2.35

## BigInt

- console.log(4838430248342043823408394839483204n); # show bigInt
- (11n / 3n) = 3n # just integer part
- 36286372637263726376237263726372632n * 10000000n # each of 2 operators must be bigInt

## Date

- const now = new Date();
- console.log(now);

- console.log(new Date('Aug 02 2020 18:05:41')); show time

- console.log(new Date(2037, 10, 19, 15, 23, 5));
- console.log(new Date(2037, 10, 31)); 

- console.log(new Date(0)); zero mili second after initializing unix time

- const future = new Date(2037, 10, 19, 15, 23);
- console.log(future);
- console.log(future.getFullYear());
- console.log(future.getMonth()); # months in js start from 0
- console.log(future.getDate()); # get day pf month
- console.log(future.getDay()); # nth day of week
- console.log(future.getHours());
- console.log(future.getMinutes());
- console.log(future.getSeconds());
- console.log(future.toISOString());
- console.log(future.getTime());

- console.log(new Date(2142256980000)); # sho date of this time
- console.log(Date.now()); # milisecond

- future.setFullYear(2040); # set time

## Operation on Dates

- const calcDaysPassed = (date1, date2) => # pass milisecond
    Math.abs(date2 - date1) / (1000 * 60 * 60 * 24); # colculate and covert to days
- calcDaysPassed(new Date(2037, 3, 4), new Date(2037, 3, 14));

## Intl

- for styling

- const now = new Date();
  const options = {
    hour: "numeric",
    minute: "numeric",
    day: "numeric",
    month: "numeric",
    year: "numeric",
    weekday: 'long',
  };    
- const locale = navigator.language;
- labelDate.textContent = new Intl.DateTimeFormat(locale, options).format(now); # new Intl.DateTimeFormat(your location, object that you want format it).format(time)

- const num = 3884764.23;
- const options = {
    style: 'currency', # 3 style we have: currency, percent, unit
    unit: 'celsius',
    currency: 'EUR',
    useGrouping: false,
  };
- console.log('US:      ', new Intl.NumberFormat('en-US', options).format(num)); # new Intl.NumberFormat(your location, object that you want format it).format(number)

## Timer

- const ingredients = ['olives', 'spinach'];
- const pizzaTimer = setTimeout(							# set 3000 ms time out  for this funcion # you can pass args of function in setTimeout: setTimeout(function, delay, args of function)
    (ing1, ing2) => console.log(`Here is your pizza with ${ing1} and ${ing2} 🍕`),
    3000,
    ...ingredients
  );
- console.log('Waiting...');
- if (ingredients.includes('spinach')) clearTimeout(pizzaTimer); # remove timeout

- setInterval(function () { # show time and update every 1000ms
  const now = new Date();
  console.log(now);
}, 1000);
