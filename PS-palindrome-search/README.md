# PS-palindrome-search exercise

## Instructions

- Using vanilla javascript, create a function that finds the second longest palindrome in a the string
- Output of the function should be as follows
  - when no palindrome exists => 'No Palindrome exists'
  - When there is only one palindrome => 'No Second Palindrome exists'
  - When there is a second palindrome => 'Found Palindrome: [PALINDROME]'
- After you complete the exercise, provide any notes on your code below such as how to run your example

## Candidate Notes:

function test2ndLongestPalindrome(str){
  var testArr = str.split("");
  var empArr = [];

  for(var i = 0; i < testArr.length; i++){
    var temp = "";
    temp = testArr[i];
    for(var j = i + 1; j < testArr.length; j++){
      temp += testArr[j];
      if(temp.length > 2 && temp === temp.split("").reverse().join("")){
        empArr.push(temp);
      }
    }
  }
  
  var count = 0;
  var secondlongestPalindrome = "";
  for(var i = 0; i < empArr.length; i++){
    if(count >= empArr[i].length){
      secondlongestPalindrome = empArr[i-2]; 
    }
    else{
    }
  }
  console.log(secondlongestPalindrome);
  return secondlongestPalindrome;
}
