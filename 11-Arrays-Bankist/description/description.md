# ARRAY-BANKIST

## Arrays Method

- arr = ['a', 'b', 'c', 'd', 'e'];
- console.log(arr.splice(2)); # splice is like slice but it cut this part of arr (index 2 to end) and mutate the arr
- console.log(arr2.reverse()); # reverse list
- const letters = arr.concat(arr2); concat
- console.log(...arr, ...arr2); # concat
- console.log(letters.join('-')); # join

## ForEach

- movements.forEach(function (movement) { # call fuction for each itrate
    if (movement > 0) {
      console.log(`you deposited ${movement}`);
    } else {
      console.log(`you withdrew ${Math.abs(movement)}`);
    }
  });

- movements.forEach(function (movement, i, arr) { # forEach by index # order of arguments: (value, index, array)
    if (movement > 0) {
      console.log(`Movement ${i + 1}: you deposited ${movement}`);
    } else {
      console.log(`Movement ${i + 1}: you withdrew ${Math.abs(movement)}`);
    }
  });

- currencies.forEach(function(value, key, map) { # map for each
    console.log(`${key}: ${value}`);
  })

- const  currenciesUnique = new Set(['USD', 'GPB', 'USD', 'EUR', 'EUR']);
- console.log(currenciesUnique);

- currenciesUnique.forEach(function(value, _, set) { set for each
    console.log(`${value}: ${value}`);
  })

## project
- containerMovements.insertAdjacentHTML('afterbegin', html); ## add element in js file
- containerMovements.innerHTML = ''; # remove html context of element in js file

- e.preventDefault(); # in forms when fill it click also by 'enter'

## Map Method

- const movementsUSD = movements.map(mov => mov * 2); # it's like for each taht you can itrate on array and do some changes

- const movementsDescriptions = movements.map(
    (mov, i) =>
      `Movement ${i + 1}: You ${mov > 0 ? 'deposited' : 'withdrew'} ${Math.abs(
        mov
      )}`
  );

## Filter Method

- const deposits = movements.filter(function (mov, i, arr) { # like for loop but with filttering by checking boolean and return
    return mov > 0;
  });

## Reduce Method

- accumulator -> SNOWBALL
    const balance = movements.reduce(function (acc, cur, i, arr) { # sum arrays element start 0
     console.log(`Iteration ${i}: ${acc}`);
     return acc + cur;
 }, 0);

## Find Method

- const firstWithdrawal = movements.find(mov => mov < 0); # return the first element that is true in condition
- console.log(movements);

## Some Method

- const anyDeposits = movements.some(mov => mov > 0); # return true or false. is there any element that greater than 0?

## Every Method

- movements.every(mov => mov > 0); # is every elemnts grater than 0?

## Separate callback

- const deposit = mov => mov > 0; # also we can declare and just pass function to methods
- console.log(movements.some(deposit));
- console.log(movements.every(deposit));
- console.log(movements.filter(deposit));

## Flat Method

- const arr = [[1, 2, 3], [4, 5, 6], 7, 8];
- arr.flat() = [1, 2, 3, 4, 5, 6, 7, 8] # remove nesteds

- const arrDeep = [[[1, 2], 3], [4, [5, 6]], 7, 8];
- arrDeep.flat(2) = [1, 2, 3, 4, 5, 6, 7, 8];

## Sorting

### String
- const owners = ['Jonas', 'Zach', 'Adam', 'Martha'];
- owners.sort(); # sort for strings. (mutate the object)

### Number
- movements.sort((a, b) => { # sorting
    if (a > b) return 1;
    if (a < b) return -1;
  });

- movements.sort((a, b) => a - b); # sorting

## From Method

- const y = Array.from({ length: 7 }, () => 1); # creatw and array with 7 length and fill it by 1

- labelBalance.addEventListener('click', function () {
    const movementsUI = Array.from(			# first arg of from = every way to get array that you want, second arg = what want to covert array to it
      document.querySelectorAll('.movements__value'),
      el => Number(el.textContent.replace('€', ''))
    );
  });