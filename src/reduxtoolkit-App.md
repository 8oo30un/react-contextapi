import React from 'react';
import {createStore} from 'redux';
import {Provider, useSelector, useDispatch} from 'react-redux';
import store from './store';
import {up} from './counterSlice';
import {down} from './counterSlice';

function Counter() {
  const dispatch = useDispatch();
  const count = useSelector((state)=>{
    return state.counter.value;});
  return (
    <div>
      <button onClick = {()=>{
        //dispatch({type: 'counterSlice/up', step : 2});
        dispatch(up(2));
      }}>+</button>
       {count}
       <button onClick = {()=>{
         dispatch(down(2));
       }}>-</button>
    </div>
  );
}

export default function App() {
  return (
    <Provider store= {store}>
    <div>
      <Counter></Counter>
    </div>
    </Provider>
  );
}
