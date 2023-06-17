# NodeJs-17-06-2023
Question 
1.	Write a JavaScript program that displays the largest integer among two integers.
Answer: 
function findLargestInteger(num1, num2) {
  if (num1 > num2) {
    return num1;
  } else {
    return num2;
  }
}

const num1 = 10;
const num2 = 20;
const largestInteger = findLargestInteger(num1, num2);
console.log("The largest integer is: " + largestInteger);

2.	Write a JavaScript function to find the sign of the product of three numbers. Display an alert box with the specified sign. 
Sample numbers : 3, -7, 2
Output : The sign is -


Answer: 
function findProductSign(num1, num2, num3) {
  var product = num1 * num2 * num3;

  if (product > 0) {
    alert("The sign is +");
  } else if (product < 0) {
    alert("The sign is -");
  } else {
    alert("The sign is 0");
  }
}

findProductSign(3, -7, 2);

3.	Write a JavaScript function to find the largest of five numbers. Display an alert box to show the results. 
Sample numbers : -5, -2, -6, 0, -1 
Output : 0

Answer: 
function findLargestNumber(num1, num2, num3, num4, num5) {
  var largest = Math.max(num1, num2, num3, num4, num5);
  alert("The largest number is: " + largest);
}

findLargestNumber(-5, -2, -6, 0, -1);

4.	Write a JavaScript program that iterates integers from 1 to 100. But for multiples of three print "Fizz" instead of the number and for multiples of five print "Buzz". For numbers multiples of both three and five print "FizzBuzz".

Answer:
for (let i = 1; i <= 100; i++) {
  if (i % 3 === 0 && i % 5 === 0) {
    console.log("FizzBuzz");
  } else if (i % 3 === 0) {
    console.log("Fizz");
  } else if (i % 5 === 0) {
    console.log("Buzz");
  } else {
    console.log(i);
  }
}

5.	According to Wikipedia a happy number is defined by the following process : "Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers, while those that do not end in 1 are unhappy numbers (or sad numbers)". Write a JavaScript program to find and print the first 5 happy numbers.

Answer
function isHappyNumber(num) {
  let sum;
  let numString = num.toString();
  let numSet = new Set();

  while (true) {
    sum = 0;
    for (let digit of numString) {
      sum += Math.pow(parseInt(digit), 2);
    }

    if (sum === 1) {
      return true;
    } else if (numSet.has(sum)) {
      return false;
    } else {
      numSet.add(sum);
      numString = sum.toString();
    }
  }
}

function findHappyNumbers(count) {
  let happyNumbers = [];
  let currentNumber = 1;

  while (happyNumbers.length < count) {
    if (isHappyNumber(currentNumber)) {
      happyNumbers.push(currentNumber);
    }
    currentNumber++;
  }

  return happyNumbers;
}

const happyNumbers = findHappyNumbers(5);
console.log("The first 5 happy numbers are: " + happyNumbers.join(", "));




6.	Write a JavaScript program to find the Armstrong numbers of 3 digits. Note : An Armstrong number of three digits is an integer such that the sum of the cubes of its digits is equal to the number itself. For example, 371 is an Armstrong number since 3**3 + 7**3 + 1**3 = 371.


Answer:
function isArmstrongNumber(num) {
  const numString = num.toString();
  const numDigits = numString.length;
  let sum = 0;

  for (let digit of numString) {
    sum += Math.pow(parseInt(digit), numDigits);
  }

  return sum === num;
}

function findArmstrongNumbers() {
  const armstrongNumbers = [];

  for (let i = 100; i < 1000; i++) {
    if (isArmstrongNumber(i)) {
      armstrongNumbers.push(i);
    }
  }

  return armstrongNumbers;
}
const armstrongNumbers = findArmstrongNumbers();
console.log("Armstrong numbers of 3 digits: " + armstrongNumbers.join(", "));

7.	Write a JavaScript program to sum 3 and 5 multiples under 1000.

Answer:
function sumMultiples() {
  let sum = 0;

  for (let i = 1; i < 1000; i++) {
    if (i % 3 === 0 || i % 5 === 0) {
      sum += i;
    }
  }

  return sum;
}


const result = sumMultiples();
console.log("The sum of multiples of 3 and 5 under 1000 is: " + result)

8	.Write a node js script using file system which will 
- create a new file 
- add data to a file
- append data to a file
- read an html file and display it on the browser

Answer:

	

const fs = require('fs');

// Create a new file
fs.writeFile('newFile.txt', 'Hello, World!', (err) => {
  if (err) throw err;
  console.log('New file created');
});

// Add data to a file
fs.writeFile('dataFile.txt', 'Data to be added', (err) => {
  if (err) throw err;
  console.log('Data added to file');
});

// Append data to a file
fs.appendFile('dataFile.txt', '\nAdditional data', (err) => {
  if (err) throw err;
  console.log('Data appended to file');
});

// Read an HTML file and display it on the browser
fs.readFile('index.html', 'utf8', (err, data) => {
  if (err) throw err;
  console.log('HTML file read');

  // Create a simple server to display the HTML content
  const http = require('http');
  const server = http.createServer((req, res) => {
    res.writeHead(200, { 'Content-Type': 'text/html' });
    res.end(data);
  });

  server.listen(3000, () => {
    console.log('Server is running on http://localhost:3000');
  });
});


9.	What is a URL. Break it down into several parts that the url consists of. Use URL module to write a nodejs script to show the breakdown parts of a url as well.


Answer:
A URL (Uniform Resource Locator) is a reference or address used to locate and access resources on the internet. It consists of several parts, each serving a specific purpose. The major parts of a URL are:

Protocol 
Host 
Port 
Path
Query Parameters 
Fragment Identifier



10.	What is a Promise in JavaScript and how does it work? Explain the states of a Promise. Explain how to chain multiple Promises together and the syntax for doing so.

Answer:
a Promise is an object that represents the eventual completion (or failure) of an asynchronous operation and its resulting value. Promises provide a way to handle asynchronous operations in a more organized and readable manner.

A Promise can be in one of three states:

Pending: The initial state when the Promise is created and waiting for the asynchronous operation to complete. At this stage, the Promise is neither fulfilled nor rejected.

Fulfilled: The state when the asynchronous operation successfully completes. The Promise transitions to the fulfilled state and holds a value or result that represents the successful completion of the operation.

Rejected: The state when the asynchronous operation fails or encounters an error. The Promise transitions to the rejected state and holds a reason or error that represents the failure of the operation.

