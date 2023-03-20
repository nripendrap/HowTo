Adding Redux library to the React project
yarn add redux react-redux redux-logger

inside src
create store folder
inside store folder create store.js file

redux middleware
store.js

import { compose, createStore, applyMiddleware } from "redux";
import logger from "redux-logger";

import { rootReducer } from "./root-reducer";

// curried function sequence of function
const loggerMiddleware = (store) => (next) => (action) => {
if(!action.type) {
return next(action)
}

console.log('type: ', action.type);
console.log('payload: ', action.payload);
console.log('currentState: ', store.getState());

next(action);
console.log('next state: ', store.getState());
}

const middleWares = [loggerMiddleware];
const composedEnhancers = compose(applyMiddleware(...middleWares));
const store = createStore(rootReducer, undefined, composedEnhancers);

export { store };

Library
Reselect
https://github.com/reduxjs/reselect
