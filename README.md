# core-code-upskilling-readme

#[⚠️Optional] Week challenges (Tuesday) 💻

//Ensure Question Exercise


const addQuestionMark = (string) => {

  const length = string.length;
  
  if (string[length - 1] === "?") {
  
    return string;
    
  } else if (string[length - 1] != "?") {
  
    string += '?';
    return string;
    
  }
  
};

console.log(addQuestionMark("Yes"));

console.log(addQuestionMark("No?"));

//Reverse Sentence

const reverseSentence = (string) => {

    const newArrayString = string.split(" ");
    
    const reversed = newArrayString.reverse().join(" ");
    
    return reversed;
}

console.log(reverseSentence('The greatest victory is that which requires no battle'))

[⚠️Optional] Week challenges (Wednesday) 💻

// Find the smallest integer in the array

const findTheSmallestArray = (array) => {

    if(array.length === 0) return "Array is empty"
    
    return array.sort(function(a, b){return a - b})[0];
}

console.log(findTheSmallestArray([34, 15, 88, 2]))

console.log(findTheSmallestArray([34, -345, -1, 100]))

console.log(findTheSmallestArray([]))

[⚠️Optional] Week challenges (Thursday) 💻
// odd or even numbers

const oddOrEven = (array) => {

  let acum = 0;
  
  array.forEach((item) => {
  
    acum += item;
    
  });
  if (acum % 2 === 0) {
  
    return "even";
    
  }else {
  
    return "odd";
    
  }


};

console.log(oddOrEven([0]));

console.log(oddOrEven([0, 1, 4]));

console.log(oddOrEven([0, -1, -5]));

////------------------------Week 2------------------------///
//---Monday--//
const isPalindrome = (string) => {
    let result = false;
    if(!string) return false;
    let newString;
    if(typeof string === 'number') {
         newString = string.toString().split('');
    } else {
        newString = string.split('');;
    }
    newString.forEach((letter,index,arr) => {
      
        if(letter != arr.reverse()[index]) {
            result =  false;
        } else if(letter === arr.reverse()[index]) {
            result = true;
        }
    })
    return result;
  

}

console.log(isPalindrome("anna")) //===> returs true
console.log(isPalindrome("walter")) //===> returs false
console.log(isPalindrome(12321)) //===> returs true
console.log(isPalindrome(123456)) //===> returs false

//---Tuesday---//

function well(x){
 if(!x) return 'No Ideas';
    let acum = 0;
    x.forEach(item => {
        if(item === 'good'){
            acum++;
        } 
    })
    if(acum >= 1 && acum <= 2){
        return 'Publish!'
    } else if(acum > 2) {
        return 'I smell a series!'
    } else{
        return 'Fail!'
    }
}

//--Wednesday--//

import {useState} from 'react'

const Test = () => {
    const [value, setValue] = useState(0)
    const onPlusClickHandler = () => {
        setValue(value + 1);
    }

    const onMinusClickHandler = () => {
        setValue(value - 1);
    }


    return (
        <main>
            <button id='increment' onClick={onPlusClickHandler}>+</button>
            <label id='counter'>{value}</label>
            <button id='decrement' onClick={onMinusClickHandler}>-</button>
        
        </main>
    )
}

export default Test;

//--Thrusday--//

import React from "react";
import { Formik } from "formik";

const SantaForm = (props) => {
  return (
    <>
      <div>
        <h1>Santa's Wishlist</h1>
        <Formik
          initialValues={{ name: "", wish: "", priority: 1 }}
          validate={(values) => {
            const errors = {};
            if (!values.name) {
              errors.name = "Required";
            } else if (!/^[a-z ,.'-]+$/i.test(values.name)) {
              errors.name = "Invalid Name";
            }
            return errors;
          }}
          onSubmit={(values, { setSubmitting }) => {
          // console.log(values)
           props.send(values)
           setSubmitting(false);
          }}
        >
          {({
            values,
            errors,
            touched,
            handleChange,
            handleBlur,
            handleSubmit,
            isSubmitting,
            /* and other goodies */
          }) => (
            <form onSubmit={handleSubmit}>
              <input
                type="text"
                name="name"
                onChange={handleChange}
                onBlur={handleBlur}
                value={values.name}
              />
              {errors.name && touched.name && errors.name}
              <textarea
                type="text"
                name="wish"
                onChange={handleChange}
                onBlur={handleBlur}
                value={values.wish}
              />
              {errors.wish && touched.wish && errors.wish}
              <select name="priority" id="priority">
                <option value="1">1</option>
                <option value="2">2</option>
                <option value="3">3</option>
                <option value="4">4</option>
              </select>
              <button type="submit" disabled={isSubmitting}>
                Submit
              </button>
            </form>
          )}
        </Formik>
      </div>
    </>
  );
};

export default SantaForm;



