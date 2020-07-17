# interview-questions

Frequency Pattern
Uses objects to collect values or frequencies of values.

const anagram = (str1, str2) => {
if (str1.length !== str2.length) {
// must be same length to be valid anagram
return false;
}

    // store chars
    let lookup = {};

    for (let i = 0; i < str1.length; i++) {
        // if char exists in lookup add 1
        // else initialize to 1
        lookup[str1[i]] ? (lookup[str1[i]] += 1) : (lookup[str1[i]] = 1);
    }

    for (let i = 0; i < str2.length; i++) {
        if (!lookup[str2[i]]) {
            // checks if char value is not 0
            return false;
        } else {
          lookup[str2[i]] -= 1;
        }
    }

    return true;

};

console.log(anagram("aazz", "zzaa"));

Multiple Pointers
Creating pointers or values that correspond to an index or position and move towards the beginning. End or middle based on a certain condition.

Example:
Write a function called sumZero which accepts a sorted array of integers. The function should find the first pair where the sum is 0. Return an array that includes both values that sum to zero or undefined if a pair does not exist.

const sumZero = arr => {
// sort array first  
 const array = [...arr].sort((a, b) => a - b);
let left = 0;
let right = array.length - 1;

    while (left < right) {
        let sum = arr[left] + arr[right];

        if (sum === 0) {
            return [arr[left], arr[right]];
        } else if (sum > 0) {
            right--;
        } else {
          left++;
        }
    }

    return undefined;

};

console.log(sumZero([-4, -3, -2, -1, 0, 1, 2, 3, 10]));

Example:
Implement a function called countUniqueValues which accepts a sorted array and counts the unique values in the array. There can be negative numbers in the array.

const sumZero = array => {
let arr = [...array].sort((a, b) => a - b);
let i = 0;

    for (let j = 1; j < arr.length; j++) {
        // j is the scout and moves forward
        if (arr[i] !== arr[j]) {
        // if i is not equal to j, add 1 to i and set it equal to j
            i++;
            arr[i] = arr[j];
        }
    }

    return i + 1;

};

console.log(sumZero([1, 2, 2, 3, 3, 3, 4, 5, 6, 6, 6, 6, 10]));

Sliding Window
Creating a window which can either be an array or number from one position to a mother. Depending on a certain condition, the window either increases or closes (and a new window is created). This is useful for keeping track of a subset of data in an array, string, etc.

Example:
Write a function called maxSubArraySum which accepts an array of integers and a number called n. The function should calculate the maximum sum of n consecutive elements in the array.

const maxSubArraySum = (arr, num) => {
let maxSum = 0;
let tempSum = 0;

    if (arr.length < num) return null;

    for (let i = 0; i < num; i++) {
        maxSum += arr[i];
    }

    tempSum = maxSum;

    for (let i = num; i < arr.length; i++) {
        // slides down the array and scans the sum of n elements
        // it subtracts the first scanned element
        // and adds the newly added element
        tempSum = tempSum - arr[i - num] + arr[i];
        // stores the largest value
        maxSum = Math.max(maxSum, tempSum);
    }

    return maxSum;

};

console.log(maxSubArraySum([1,32,35,25,1,4,36,1,23,34], 3));

Divid and Conquer
Dividing a data set into smaller chunks and then repeating a process with a subset of data. This pattern can tremendously decrease time complexity.
