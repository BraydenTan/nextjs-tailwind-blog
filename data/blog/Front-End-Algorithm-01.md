---
title: Basic Leetcode with JavaScript 1
date: '2023-05-13'
tags: ['LeetCode', 'JavaScript', 'Algorithm']
draft: false
summary: Basic Foundation using JavaScipt for LeetCode
images:
  [
    https://elasticbeanstalk-ap-southeast-1-733447040549.s3.ap-southeast-1.amazonaws.com/Leetcodejavascript01.jpeg,
  ]
layout: PostLayout
canonicalUrl: frontentleetcode01
---

## Introduction

**Introducing Algorithm with JavaScript, Array ,String,Traversal,Higher-order function,Regular expression and related math theory.**

```md
Content Include

- Array
- String
- Traversal
- Higher-order Function
- Regular expression
- Related Math
```

## Common 13 methods of arrays

**1 Push()**

Push will append to the end, similar to stacking, and the original array will be modified.

```js
const arr = [1, 2, 3]
arr.push(8)
console.log(arr) // [1, 2, 3, 8]
```

**2 pop()**

Pop from the end, similar to popping out from a stack, and the original array will be modified. The push & pop of an array can simulate one of the common data structures: stack (Stack).

```js
const arr = [1, 2, 3]
const popVal = arr.pop()
console.log(popVal) // 3
console.log(arr) // [1, 2]

// Arrays simulate one of the common data structures: stack (Stack)
const stack = [0, 1]
stack.push(2) // Pushing to the stack
console.log(stack) // [0, 1, 2]

const popValue = stack.pop() // popping from the stack
console.log(popValue) // 2
console.log(stack) // [0, 1]
```

**3 unshift()**

Unshift will add data to the beginning, similar to enqueuing, and the original array will be modified.

```js
const arr = [1, 2, 3]
arr.unshift(0)
console.log(arr) // [0, 1, 2, 3]
```

**4 shift()**

Shift will remove data from the beginning, and the original array will be modified. The push (enqueuing) & shift (dequeuing) of an array can simulate one of the common data structures: queue (Queue).

```js
const arr = [1, 2, 3]
const shiftVal = arr.shift()
console.log(shiftVal) // 1
console.log(arr) // [2, 3]

// Array simulation of one of the common data structures: queue (Queue).
const queue = [0, 1]
queue.push(2) // Enqueuing
console.log(queue) // [0, 1, 2]

const shiftValue = queue.shift() // Dequeuing
console.log(shiftValue) // 0
console.log(queue) // [1, 2]
```

**5 concat()**

Concat will concatenate the passed-in array to the end of the current array, then return a new array. The original array remains unchanged.

```js
const arr = [1, 2, 3]
const arr2 = arr.concat([7, 8, 9])
console.log(arr) // [1, 2, 3]
console.log(arr2) // [1, 2, 3, 7, 8, 9]
```

**6 indexOf()**

"indexOf" method in an array can be used to find the index of a given value in the array. If the value is found, the method will return the index of the value. If the value is not found, the method will return -1.

```js
const arr = [1, 2, 3]
console.log(arr.indexOf(2)) // 1
console.log(arr.indexOf(0)) // -1
```

**7 include()**

Find the value in the array. If found, return true, otherwise return false.

```js
const arr = [1, 2, 3]
console.log(arr.includes(2)) // true
console.log(arr.includes(4)) // false
```

**8 join()**

The join() method converts an array into a string with a specified separator and returns that string. If no separator is provided, the default separator is a comma. The original array is not modified.

```js
const arr = [1, 2, 3]
console.log(arr.join()) // ‘1, 2, 3’
console.log(arr) // [1, 2, 3]
```

**9 reverse()**

Reverse the original array and return the reversed array. The original array is mutated.

```js
const arr = [1, 2, 3]
console.log(arr.reverse()) // [3, 2, 1]
console.log(arr) // [3, 2, 1]
```

**10 slice(start,end)**

returns a new array that includes elements from the starting index up to but not including the ending index.

```js
const arr = [1, 2, 3, 4, 5]
console.log(arr.slice(1, 4)) // [2, 3, 4]
console.log(arr) // [1, 2, 3, 4, 5]
```

**11 splice(start, deleteCount, item1, item2……)**

- The start parameter specifies the starting position.
- deleteCount indicates the number of elements to be removed.
- The items following deleteCount are the elements to be added.
- If deleteCount is set to 0, it means no elements will be deleted, and the elements after start will be added to the original array.
- The return value is an array consisting of the deleted elements. If only one element is deleted, the return value will be an array containing only that element. If no elements are deleted, an empty array is returned.
- This method modifies the original array and changes its length.

```js
const arr3 = [1, 2, 3, 4, 5, 6, 7, 'f1', 'f2']
const arr4 = arr3.splice(2, 3) // Remove element after third array elements (including the third element) .
console.log(arr4) // [3, 4, 5];
console.log(arr3) // [1, 2, 6, 7, "f1", "f2"]; Original Array will changed

const arr5 = arr3.splice(2, 0, 'wu', 'leon')
// Remove 0 elements starting from the second position, and insert "wu" and "leon".
console.log(arr5) // [] Return empty array
console.log(arr3) // [1, 2, "wu", "leon", 6, 7, "f1", "f2"]; Original array will changed

const arr6 = arr3.splice(2, 3, 'xiao', 'long')
// Starting from the second position （0，1，2）, delete three elements and insert "xiao" and "long". the three deleted element will be in arr6
console.log(arr6) // ["wu", "leon", 6]
console.log(arr3) //[ 1, 2, "xiao", "long", 7, "f1", "f2"]

const arr7 = arr3.splice(2) // delete from third element
console.log(arr7) // ["xiao", "long", 7, "f1", "f2"]
console.log(arr3) // [1, 2]
```

**12 sort()**

- Sorts the elements and returns the array.
- The default sort order is built upon converting the elements into strings, then comparing their sequences of UTF-16 code units values.
- Because the implementation-dependent, it is impossible to guarantee the time and space complexity of the sort. For more information, please refer to[MDN：Sort](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

```js
const arr = [1, 2, 3]
arr.sort((a, b) => b - a)
console.log(arr) // [3, 2, 1]
```

**13 toString()**

Convert the array to a string, separated by commas, and return the resulting string. The original array will not be modified.

```js
const arr = [1, 2, 3, 4, 5]
console.log(arr.toString()) // ‘1, 2, 3, 4, 5’
console.log(arr) // [1, 2, 3, 4, 5]
```

## <u>Common 12 String Methods</u>

**1 charAt()**

Returns the character at the specified index position. Similar to accessing data at the corresponding index position in an array using square brackets.

```js
var str = 'abcdefg'
console.log(str.charAt(2)) // OUTPUT 'c'
console.log(str[2]) // OUTPUT 'c'
```

**2 concat()**

Similar to the concat() method of arrays, it is used to return a new string that concatenates two or more strings. The original strings are not changed.

```js
const str1 = 'abcdefg'
const str2 = '1234567'
const str3 = str1.concat(str2)
console.log(str3) // OUTPUT 'abcdefg1234567'
```

**3 indexOf()、lastIndexOf()**

"indexOf" returns the first occurrence of a character in a string, while "lastIndexOf" returns the last occurrence of a character in a string.

```js
const str = 'abcdcefcg'
console.log(str.indexOf('c')) // OUTPUT '2'
console.log(str.lastIndexOf('c')) // OUTPUT '7'
```

**4 slice()**

Extract a portion of a string and return the extracted string as a new string. The original string remains unchanged.

```js
const str = 'abcdefg'
console.log(str.slice()) // To output 'abcdefg', if no arguments are passed, the entire string is copied.
console.log(str.slice(1)) // To output 'bcdefg' by passing one parameter, which is the starting point of the extraction and goes to the end of the string.
console.log(str.slice(2, str.length - 1)) // "Output 'cdef', pass two parameters: the starting point and the end point of the extracted substring."
```

**5 split()**

Split a string into an array of multiple substrings using a specified separator, and return the new array. The original string remains unchanged.

```js
const str = 'A*B*C*D*E*F*G'
console.log(str.split('*')) // OUTPUT ["A", "B", "C", "D", "E", "F", "G"]
```

**6 substr(), substring()**

- These two methods are used to extract a substring from a string and return it.
- The difference between substr and substring lies in the second parameter. The second parameter of substr is the length of the substring to be returned, while the second parameter of substring is the end point of the substring to be returned, and does not include this end point. They both have the same functionality for the first parameter, which is the starting position of the substring to be extracted.
- Note: if the second parameter of substr is 0 or negative, an empty string is returned. If it is not provided, it will extract the substring to the end of the string. If the first or second parameter of substring is NaN or negative, it will be replaced with 0.

```js
const str = 'ABCDEFGHIJKLMN'
console.log(str.substr(2)) // OUTPUT 'CDEFGHIJKLMN'
console.log(str.substring(2)) // OUTPUT 'CDEFGHIJKLMN'

console.log(str.substr(2, 9)) // OUTPUT 'CDEFGHIJK'为什么是K因为从C开始算
console.log(str.substring(2, 9)) // OUTPUT 'CDEFGHI'
```

**7 match()**

The match() method can search for a specified value or find one or more matches of a regular expression within a string, and then return an array containing the search results.

```js
const str = '2018End，2019start，2020年soon'
const reg = /\d+/g // Here is the definition of the matching rule, which matches one or more digits in a string.
console.log(str.match(reg)) // Output the content that matches the matching rules, and return it in an array format ['2018', '2019', '2020'].
console.log(str.match('20')) // It does not use regular expressions.['20', index: 0, input: '2018End，2019start，2020年soon',
```

Note: If the match method does not find a match, it will return null. If a match is found, the match method will return the match as an array. If the regular expression pattern does not have the global modifier 'g', the returned array will have two properties: input and index. The input property contains the entire string that was searched. The index property contains the position of the matched substring within the entire searched string.

**8 replace()**

replace method takes two parameters. The first parameter is the character or regular expression pattern that needs to be replaced, and the second parameter is the character to be replaced with. In the actual implementation, you can replace the second parameter with a callback function.

```js
const str = '2018年结束了，2019年开始了，2020年就也不远了'
const rex = /\d+/g // 这里是定义匹配规则，匹配字符串里的1到多个数字
const str1 = str.replace(rex, '****')
console.log(str1) // 输出："****年结束了，****年开始了,****年也不远了"
const str2 = str.replace(rex, function (item) {
  console.log(arguments) // 看下面的图片
  const arr = ['零', '壹', '贰', '叁', '肆', '伍', '陆', '柒', '捌', '玖']
  let newStr = ''
  item.split('').map(function (i) {
    newStr += arr[i]
  })
  return newStr
})
console.log(str2) // 输出：贰零壹捌年结束了，贰零壹玖年开始了,贰零贰零年也不远了
```

**9 search()**

Searches for a match between a regular expression and the target string. If a match is found, the indexOf() method returns the index of the first match. If no match is found, it returns -1.

```js
const str = '2018年结束了，2019年开始了，2020年就也不远了'
const reg = /\d+/i // 这里是定义匹配规则,匹配字符串里的1到多个数字
console.log(str.search(reg)) // 输出 0  这里搜索到的第一项是从位置0开始的
```

**10 toLowerCase(),toUpperCase()**

The toLowerCase() method converts letters to lowercase, while toUpperCase() converts letters to uppercase.

```js
const str1 = 'abcdefg'
const str2 = 'ABCDEFG'
console.log(str2.toLowerCase()) // OUTPUT：'abcdefg'
console.log(str1.toUpperCase()) // OUTPUT：'ABCDEFG'
```

**11 includes(), startsWith(), endsWith()**

'includes', 'startsWith', and 'endsWith' are new methods in ES6. 'includes' is used to check whether a target string contains a certain character and returns a Boolean value. 'startsWith' is used to check whether the current character is the starting part of the target string. On the other hand, 'endsWith' is used to check whether it is the ending part of the target string.

```js
const str = 'Excuse me, how do I get to park road?'
console.log(str.includes('how')) // 输出：true
console.log(str.startsWith('Excuse')) // 输出： true
console.log(str.endsWith('?')) // 输出： true
```

**12 repeat()**

"Return a new string object which is equal to the original string repeated a specified number of times. It takes one parameter, which specifies the number of times to repeat the string. The original string remains unchanged."

```js
const str = 'http'
const str2 = str.repeat(3)
console.log(str) // 输出：'http'
console.log(str2) // 输出：'httphttphttp'
```

## <u>11 Traversal & higher-order functions</u>

**1 for()**

The most commonly used method for traversal is the for loop, which is frequently used for array traversal and can also be used to traverse strings.

```js
const arr = [1, 2, 3]
const str = 'abc'
for (let i = 0; i < arr.length; i++) {
  console.log(arr[i])
  console.log(str[i])
}
```

**2.while() / do while()**

While and do-while loops are mainly used to execute certain tasks when the condition specified after while is satisfied. The difference between these two is that while first checks if the condition is satisfied and then executes the tasks inside the curly braces, whereas do-while first executes the tasks inside the curly braces and then checks the condition specified after while to determine whether to execute the tasks inside the curly braces again. Therefore, do-while loop will execute the tasks inside the curly braces at least once.

```js
while(Condition){
     Execute...
}
------------
do{
    Execute...
}
while(Condition)
```

**3 forEach()**

Copy and traverse the original array.

- "return" cannot terminate the loop. However, it can have the effect of "continue".
- "continue" and "break" statements are not supported, but we can achieve similar effects using "some" and "every" methods.

```js
const arr = [5, 1, 3, 7, 4]
arr.forEach((item, index) => {
  if (item < 2) return
  console.log(`索引：${index}，数值：${item}`)
  arr[5] = 0
})
console.log(arr)
// 打印结果：
// 索引：0，数值：5
// 索引：2，数值：3
// 索引：3，数值：7
// 索引：4，数值：4
// [5, 1, 3, 7, 4, 0]
```

**4 for...in**

- for...in is an ES5 standard, which has lower efficiency in iterating over arrays, and is mainly used to iterate over object properties.
- The disadvantage of iterating over arrays: the index values of the array are numbers, but the index values iterated by for-in are strings, such as "0", "1", "2", etc.
- Object.defineProperty creates a property that is not enumerable by default.

```js
const foo = {
  name: 'bar',
  sex: 'male',
}
Object.defineProperty(foo, 'age', { value: 18 })
for (const key in foo) {
  console.log(`可枚举属性：${key}`)
}
console.log(`age属性：${foo.age}`)
// 打印结果：
// 可枚举属性：name
// 可枚举属性：sex
// age属性：18
```

**5 for...of**

for...of is a new method introduced in ES6, but it cannot be used to iterate over regular objects. The benefit of for...of is that it allows the use of break to exit the loop.

- The for...of method avoids all the pitfalls of the for...in loop.
- Unlike forEach(), it correctly responds to break, continue, and return statements.
- The for...of loop not only supports arrays, but also supports most array-like objects, such as DOM NodeList objects.
- The for...of loop also supports string iteration.

```js
// for of 循环直接得到的就是值
const arr = [1, 2, 3]
for (const value of arr) {
  console.log(value)
}
```

面试官：说一下 for...in 和 for...of 区别？

```js
（1）for…in 用于可枚举数据，如对象、数组、字符串
（2）for…of 用于可迭代数据，如数组、字符串、Map、Set
```

**6.every / some**

返回一个布尔值。当我们需要判定数组中的元素是否都满足某些条件时，可以使用 every / some。这两个的区别是，every 会去遍历判断是否数组中的每一项都满足条件，遇到不满足的直接停止遍历返回 false，而 some 则是当某一项满足条件时停止遍历，返回 true。

```js
// every
const foo = [5, 1, 3, 7, 4].every((item, index) => {
  console.log(`索引：${index}，数值：${item}`)
  return item > 2
})
console.log(foo)
// every 打印：
// 索引：0，数值：5
// 索引：1，数值：1
// false
```

```js
// some
const foo = [5, 1, 3, 7, 4].some((item, index) => {
  console.log(`索引：${index}，数值：${item}`)
  return item > 2
})
console.log(foo)
// some 打印：
// 索引：0，数值：5
// true
```

**7 filter()**

- filter 方法用于过滤数组成员，满足条件的成员组成一个新数组返回。
- 它的参数是一个函数，所有数组成员依次执行该函数，返回结果为 true 的成员组成一个新数组返回。
- 该方法不会改变原数组。

```js
const foo = [5, 1, 3, 7, 4].filter((item, index) => {
  console.log(`索引：${index}，数值：${item}`)
  return item > 2
})
console.log(foo)
// 打印结果：
// 索引：0，数值：5
// 索引：1，数值：1
// 索引：2，数值：3
// 索引：3，数值：7
// 索引：4，数值：4
// [5, 3, 7, 4]
```

**8 map()**

- map 即是 “映射”的意思 ，原数组被“映射”成对应新数组。
- map：支持 return，相当与原数组克隆了一份，把克隆的每项改变了，也不影响原数组。

```js
const foo = [5, 1, 3, 7, 4].map((item, index) => {
  console.log(`索引：${index}，数值：${item}`)
  return item + 2
})
console.log(foo)
// 打印结果：
// 索引：0，数值：5
// 索引：1，数值：1
// 索引：2，数值：3
// 索引：3，数值：7
// 索引：4，数值：4
// [7, 3, 5, 9, 6]
```

**9 reduce() / reduceRight()**

reduce 从左到右将数组元素做“叠加”处理，返回一个值。reduceRight 从右到左。

```js
const foo = [5, 1, 3, 7, 4].reduce((total, cur) => {
  console.log(`叠加：${total}，当前：${cur}`)
  return total + cur
})
console.log(foo)
// 打印结果：
// 叠加：5，当前：1
// 叠加：6，当前：3
// 叠加：9，当前：7
// 叠加：16，当前：4
// 20
```

**10.Object.keys 遍历对象的属性**

Object.keys 方法的参数是一个对象，返回一个数组。该数组的成员都是该对象自身的（而不是继承的）所有属性名，且只返回可枚举的属性。

```js
const obj = {
  p1: 123,
  p2: 456,
}
Object.keys(obj) // ["p1", "p2"]
```

**11.Object.getOwnPropertyNames() 遍历对象的属性**

Object.getOwnPropertyNames 方法与 Object.keys 类似，也是接受一个对象作为参数，返回一个数组，包含了该对象自身的所有属性名。但它能返回不可枚举的属性。

```js
const arr = ['Hello', 'World']
Object.keys(arr) // ["0", "1"]
Object.getOwnPropertyNames(arr) // ["0", "1", "length"]
```

**以上遍历方法的区别：**

```js
一：map()，forEach()，filter()循环的共同之处：
  1.forEach，map，filter循环中途是无法停止的，总是会将所有成员遍历完。
  2.他们都可以接受第二个参数，用来绑定回调函数内部的 this 变量，将回调函数内部的 this 对象，指向第二个参数，间接操作这个参数（一般是数组）。

二：map()、filter()循环和forEach()循环的不同：
   forEach 循环没有返回值； map，filter 循环有返回值。

三：map()和filter()都会跳过空位，for 和 while 不会

四：some()和every():
   some()只要有一个是true，便返回true；而every()只要有一个是false，便返回false.

五：reduce()，reduceRight()：
   reduce是从左到右处理（从第一个成员到最后一个成员），reduceRight则是从右到左（从最后一个成员到第一个成员）。

六：Object对象的两个遍历 Object.keys 与 Object.getOwnPropertyNames：
   他们都是遍历对象的属性，也是接受一个对象作为参数，返回一个数组，包含了该对象自身的所有属性名。但Object.keys不能返回不可枚举的属性；Object.getOwnPropertyNames能返回不可枚举的属性。

```

## <u>Regular expression 常用正则表达式</u>

这里罗列一些我在刷算法题中遇到的正则表达式，如果有时间可认真学一下[正则表达式不要背](https://juejin.cn/post/6844903845227659271#heading-0)

**1.判断字符**

```js
由26个英文字母组成的字符串：^[A-Za-z]+$
由26个大写英文字母组成的字符串：^[A-Z]+$
由26个小写英文字母组成的字符串：^[a-z]+$
由数字和26个英文字母组成的字符串：^[A-Za-z0-9]+$
```

**2.判断数字**

```js
数字：^[0-9]*$
```

**3 持续更新，敬请期待……**

## <u>五、数学知识</u>

**1.质数**

若一个正整数无法被除了 1 和它自身之外的任何自然数整除，则称该数为质数（或素数），否则称该正整数为合数。

```js
function judgePrime(n) {
  for (let i = 2; i * i <= n; i++) {
    if (n % i == 0) return false
  }
  return true
}
```

**2.斐波那契数列**

```js
function Fibonacci(n) {
  if (n <= 1) return n
  return Fibonacci(n - 1) + Fibonacci(n - 2)
}
```

**3.其他 [刷算法题必备的数学考点汇总](https://zhuanlan.zhihu.com/p/301338035)**
