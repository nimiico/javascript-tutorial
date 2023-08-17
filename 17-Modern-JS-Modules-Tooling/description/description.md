# Moddern, JS, Modules, Tooling

- application develope: modules, 3rd party packages(leaflet, react, ... -> bundling modules in to 1 file(by Parcel) -> Babel( convert application to be available on ES5 browsers (by parcel)

- when we want use modules in our code, we need to add type='moule' to <script element>
- we do not need to use strict mode on top of our code when we use modules

## named export and import

- export { totalPrice, totalQuantity as tq }; # exporting vaiables
- import { addToCart, totalPrice as price, tq } from './shoppingCart.js'; # importing vaiables

- import \* as ShoppingCart from './shoppingCart.js';

## Default export

- export default function (product, quantity) {} # it can have any name in file that will be imported because it will be as default export
- import add from './shoppingCart.js'; # import default export

## CommonJS Modules

- these are use in Node.js

### Export

- export.addTocart = function (product, quantity) {
  cart.push({ product, quantity });
  console.log(
  `${quantity} ${product} added to cart (sipping cost is ${shippingCost})`
  );
  };

### Import

- const { addTocart } = require('./shoppingCart.js');

## NPM (Node Package Manager)

1. npm init # initialize it in project and wiil create package.json file. this file includes our npm config
2. npm install <library name> # we can install library by this code instead of write a <script> in html file (we do this in Mapty project). by installing a package, the name of the package will be add to dependencies in package.json file

- npm install # install all libraries that thei name is in dependenceis, so we can do not send packages folder to github or anywhere.

### lodash-es library

- npm install lodash-es
- import cloneDeep from 'lodash-es';
- const stateClone = Object.assign({}, state); # copy of object but it is not deep
- const stateDeepClone = cloneDeep(state); # create deep copy of object

### parcel

1. npm install parcel --save-dev # it is add to devDependencies because we can use it to develope our project
2. npx parcel <html file that you write <script filename.js> > # bundling # brfore it we must delete type='module from script because modules do not work on older browsers
3. by above code, a folder(dist) is created that has new files that are bundled

- "start": "parcel index.html" # we can write this code in script block of package.json
- npm run start # similar to: npx parcel index.html

- "build": "parcel build index.html" # we can write this code in script block of package.json
- npm run build # build

- if (module.hot) { # do not allow to reload page, when we change code
  module.hot.accept();
  }

## Babel

- npm i core-js
- import 'core-js/stable' # polyfilling # stable to ES5

- npm i regenerator-runtime
- import 'regenerator-runtime/runtime' # polyfiliing async functions

## clean Code

- read at images

## Imperative vs Declarative

- imperative -> How do things, step by step
- declarative -> what to do
