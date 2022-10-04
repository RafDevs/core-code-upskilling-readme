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

// Week 3 //

// Monday //

// Search Component //
import React,  {useState}  from "react";
import classes from "./Search.module.css";

const Search = (props) => {
    const [searchKey , setSearchKey] = useState('');
    const handleOnChange = (e) => {
        setSearchKey(e.target.value);
    }
    const filtered = props.data.filter((value) => {
        return value.toLowerCase().includes(searchKey.toLowerCase());
    })
  return (
    <>
      <div className={classes.center}>
        <input type="text" placeholder="Search items" onChange={handleOnChange}></input>
      
      </div>
      <div className={classes.list}>
        <div>
        {filtered.map((items) => (
          <li key={Math.random()}>{items}</li>
        ))}
        </div>
      </div>
    </>
  );
};

export default Search;

// app.js component // 
import Search from './Components/Search'

function App() {
  
  const data = ['Banana', 'Apple', 'Orange', 'Mango', 'Pineapple', 'Watermelon']
  return (
    <div>
      <Search data = {data} />
    </div>
  );
}

export default App;


// Styles //
.center {
    display: flex;
    justify-content: center;
}

.center input {
    margin-top: 15%;
    width: 20%;
    padding: 1rem;
    text-align: center;
    font-size:1rem;
    font-weight: bold;

}

.list{
    display: flex;
    justify-content: center;
  margin-top: 1rem;
}

li {
    list-style: none;
    margin-top: 1rem;
    text-align: center;
}


// Tuesday //

import React, {useState, useEffect} from "react";
import classes from './FetchRandomUser.module.css'
const FetchRandomUser = () => {
    const [userData, setUserData] = useState({})
  const generateData = async() => {
    const random = Math.floor(Math.random() * 10) +1;
    const data = await fetch(`https://jsonplaceholder.typicode.com/users/${random}`);
    const jsonResponse = await data.json();
    setUserData(jsonResponse);

   
  };

  useEffect(() => {
    generateData();
  }, [])
  return <div>
   <button onClick={generateData}>Fetch</button>
   <ul className={classes.list}>
    <li><span>name:</span>{userData.name}</li>
    <li><span>website:</span>{userData.website}</li>
    <li><span>email:</span>{userData.email}</li>
    <li><span>phone:</span>{userData.phone}</li>
   </ul>
   
  </div>;
};

export default FetchRandomUser;

// styles //

.list {
    list-style-type: none;

}

.list span {
    text-transform: capitalize;
    font-weight: bold;
    margin-right: 1rem;
}

//Wednesday //

// Blog component //
import react from 'react';
import {Link} from 'react-router-dom'
const Blog = (props) => {


    return (<>
    {props.reference === 'React' && (
    <>
        <h1>{props.blog.React.name}</h1>
        <p>{props.blog.React.content}</p>
        <Link to='/'>👈 Back</Link>
        </>
    )}
    {props.reference === 'Core-Code' && (
    <>
        <h1>{props.blog.CoreCode.name}</h1>
        <p>{props.blog.CoreCode.content}</p>
        <Link to='/'>👈 Back</Link>
        </>
    )}
    {props.reference === 'Hello-World' && (
    <>
        <h1>{props.blog.HelloWorld.name}</h1>
        <p>{props.blog.HelloWorld.content}</p>
        <Link to='/'>👈 Back</Link>
        </>
    )}
    </>)
    
}

export default Blog;

// app.js component // 



import {BrowserRouter as Router, Route, Routes} from "react-router-dom"
import Blog from './Components/Blog'
import Home from './Components/Home'
function App() {
  const blogs = {
    React: { 
    name: 'React',
      content: 'Suspendisse id dolor massa. Mauris eleifend nisi ante, nec consectetur, lectus arcu imperdiet ligula, in mollis enim lacus sit amet arcu. Aenean bibendum auctor nunc. Nulla facilisi. Quisque ullamcorper tellus ipsum, eu blandit neque tristique vel. Mauris fermentum nec nisl at euismod. Integer fringilla, ligula eget faucibus pellentesque, lectus sapien egestas tortor, in consequat purus velit quis dui. Aenean vestibulum mi a eleifend euismod. In quis massa maximus, dictum tortor ac, bibendum felis. Donec dictum erat dui, id rhoncus metus commodo eu. Aliquam tempus at augue quis rhoncus.',
    },
     CoreCode:{ name: 'Core Code',
      content: 'Lorem ec volutpat urna sodales id. Aenean consectetur, turpis vitae blandit consectetur, lectus arcu imperdiet ligula, in mollis enim lacus sit amet arcu. Aenean bibendum auctor nunc. Nulla facilisi. Quisque ullamcorper tellus ipsum, eu blandit neque tristique vel. Mauris fermentum nec nisl at euismod. Integer fringilla, ligula eget faucibus pellentesque, lectus sapien egestas tortor, in consequat purus velit quis dui. Aenean vestibulum mi a eleifend euismod. In quis massa maximus, dictum tortor ac, bibendum felis. Donec dictum erat dui, id rhoncus metus commodo eu. Aliquam tempus at augue quis rhoncus.',
    },
     HelloWorld: { name: 'Hello World',
      content: 'bibendum felis. Donec dictum erat dui, id rhoncus metus commodo eu. Aliquam tempus at augue quis rhoncus.',
  },
}
  
  

  return (
    <Router>
      
      <Routes>
        <Route exact path='/' element={<Home/>}/>
        <Route exact path='/React' element={<Blog blog= {blogs} reference='React'/>} />
        <Route exact path='/Core-Code'element={<Blog blog= {blogs} reference='Core-Code'/>} />
        <Route exact path='/Hello-World'element={<Blog blog= {blogs} reference='Hello-World'/>} />
      </Routes>
    </Router>
  );
}

export default App;


// Styles Home //

.list {
    font-weight: bold;
   
}

.list p {
    font-weight: normal;
}


// Thrusday //

/* redux Lecture */

