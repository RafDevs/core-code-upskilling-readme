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


