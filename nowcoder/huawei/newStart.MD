# HJ4 字符串分隔

https://www.nowcoder.com/practice/d9162298cb5a437aad722fccccaae8a7?tpId=37&tags=&title=&difficulty=0&judgeStatus=0&rp=1&sourceUrl=%2Fexam%2Foj%2Fta%3FtpId%3D37

```js
const rl = require("readline").createInterface({ input: process.stdin });
var iter = rl[Symbol.asyncIterator]();
const readline = async () => (await iter.next()).value;

void (async function () {
  // Write your code here

  let line = await readline();

  if (line.length > 8) {
    for (let i = 0; i < line.length; i += 8) {
      if (line.length - i >= 8) {
        console.log(line.split("").splice(i, 8).join(""));
      }
      // break
    }
    let temp = line.length % 8;
    let n = "";
    for (let i = 0; i < 8 - temp; i++) {
      n += "0";
    }
    if (temp != 0) {
      console.log(
        line
          .split("")
          .splice(line.length - temp, line.length)
          .concat(new Array(8 - temp).fill("0"))
          .join("")
      );
    } else {
      console.log(
        line
          .split("")
          .splice(line.length - temp, line.length)
          .join("")
      );
    }
  } else if (line.length == 8) {
    console.log(line);
  } else if (line.length < 8) {
    let newArr = line.split("");
    let add0 = 8 - newArr.length;
    let str0 = "";
    for (let i = 0; i < add0; i++) {
      str0 += "0";
    }
    newArr.push(str0);
    console.log(newArr.join(""));
  }
})();
```

# HJ5 太简单了 不写了

# HJ6 HJ6 质数因子

https://www.nowcoder.com/practice/196534628ca6490ebce2e336b47b3607?tpId=37&tags=&title=&difficulty=0&judgeStatus=0&rp=1&sourceUrl=%2Fexam%2Foj%2Fta%3FtpId%3D37

```js
const rl = require("readline").createInterface({ input: process.stdin });
var iter = rl[Symbol.asyncIterator]();
const readline = async () => (await iter.next()).value;
const getLine = (line, newLine, logArr) => {
  // console.log(line,'line')
  if (line === 0) {
    console.log("0 1");
    return;
  }
  if (line === 1) {
    console.log("1");
    return;
  }
  for (let i = 2; i < line; i++) {
    if (line % i == 0) {
      newLine = line / i;
      logArr.push(i);
      getLine(newLine, undefined, logArr);
      return;
    }
  }
  logArr.push(line);
};
void (async function () {
  let num = await readline();
  let line = Number(num);
  let newLine = undefined;
  let logArr = [];
  getLine(line, newLine, logArr);
  // console.log(logArr,'logArr')
  console.log(logArr.join(" "));
})();
// 我的例子通过了 11/12 这块写的没问题，但是算法不够好 只能说能实现需求
// 原因是超时了
// 示例代码
const rl = require("readline").createInterface({ input: process.stdin });
var iter = rl[Symbol.asyncIterator]();
const readline = async () => (await iter.next()).value;

void (async function () {
  // Write your code here,
  let num = (originNum = Number(await readline()));
  const sqrt = parseInt(Math.sqrt(num)); //开方 没看懂为啥要开方 这是个技巧吧
  let res = "";
  for (let i = 2; i <= sqrt; i++) {
    // while 循环主体 循环完 num / i res +=i + ''
    while (num % i === 0) {
      res += i + " ";
      num /= i;
    }
    if (num < i) break;
  }
  num > sqrt && (res += num + " "); //拼接
  console.log(res);
})();
// 质数的概念 https://zhuanlan.zhihu.com/p/113815619
// 看了下质数的概念 好像他这还有bug
```

# HJ7 取近似值

https://www.nowcoder.com/practice/3ab09737afb645cc82c35d56a5ce802a?tpId=37&tags=&title=&difficulty=0&judgeStatus=0&rp=1&sourceUrl=%2Fexam%2Foj%2Fta%3FtpId%3D37

```js
// 法1
const rl = require("readline").createInterface({ input: process.stdin });
var iter = rl[Symbol.asyncIterator]();
const readline = async () => (await iter.next()).value;

void (async function () {
  let line = await readline();
  let tokens = line.split(".");
  let one = tokens[1].charAt(0);
  if (parseInt(one) >= 5) {
    console.log(+tokens[0] + 1);
  } else {
    console.log(+tokens[0]);
  }
})();
// 法2
void (async function () {
  let line = await readline();
  let tokens = line.split(".");
  let one = [0, ".", tokens[1]].join("");
  if (Number(one) >= 0.5) {
    console.log(+tokens[0] + 1);
  } else {
    console.log(+tokens[0]);
  }
})();
```

# HJ8 合并表记录

https://www.nowcoder.com/practice/de044e89123f4a7482bd2b214a685201?tpId=37&tags=&title=&difficulty=0&judgeStatus=0&rp=1&sourceUrl=%2Fexam%2Foj%2Fta%3FtpId%3D37

```js
const rl = require("readline").createInterface({ input: process.stdin });
var iter = rl[Symbol.asyncIterator]();
const readline = async () => (await iter.next()).value;

void (async function () {
  let line = await readline();
  let res = [];
  for (let i = 0; i < line; i++) {
    item = await readline();
    let tokens = item.split(" ");
    let index = parseInt(tokens[0]);
    let value = parseInt(tokens[1]);
    if (res[index]) {
      res[index] += +value;
    } else {
      res[index] = +value;
    }
  }
  for (let i = 0; i < res.length; i++) {
    if (res[i]) {
      console.log(i + " " + res[i]);
    }
  }
})();
// 这个题主要考哈希表 但是在js中 数组就是哈希表 直接用就行了 那如果不用这个特性呢？
```

# HJ9 提取不重复的整数

https://www.nowcoder.com/practice/253986e66d114d378ae8de2e6c4577c1?tpId=37&tags=&title=&difficulty=0&judgeStatus=0&rp=1&sourceUrl=%2Fexam%2Foj%2Fta%3FtpId%3D37

```js
// 用set秒了
const rl = require("readline").createInterface({ input: process.stdin });
var iter = rl[Symbol.asyncIterator]();
const readline = async () => (await iter.next()).value;

void (async function () {
  // Write your code here
  let line = await readline();
  let tokens = line.split("").reverse();
  console.log([...new Set(tokens)].join(""));
})();
```

# HJ10 字符个数统计

https://www.nowcoder.com/practice/eb94f6a5b2ba49c6ac72d40b5ce95f50?tpId=37&tags=&title=&difficulty=0&judgeStatus=0&rp=1&sourceUrl=%2Fexam%2Foj%2Fta%3FtpId%3D37

```js
const rl = require("readline").createInterface({ input: process.stdin });
var iter = rl[Symbol.asyncIterator]();
const readline = async () => (await iter.next()).value;

void (async function () {
  // Write your code here
  let line = await readline();
  let tokens = line.split("");
  console.log([...new Set(tokens)].join("").length);
})();
```

# HJ11 数字颠倒

https://www.nowcoder.com/practice/ae809795fca34687a48b172186e3dafe?tpId=37&tags=&title=&difficulty=0&judgeStatus=0&rp=1&sourceUrl=%2Fexam%2Foj%2Fta%3FtpId%3D37

```js
const rl = require("readline").createInterface({ input: process.stdin });
var iter = rl[Symbol.asyncIterator]();
const readline = async () => (await iter.next()).value;

void (async function () {
  // Write your code here
  let line = await readline();
  let tokens = line.split("").reverse().join("");
  console.log(tokens);
})();
```

# HJ1 字符串最后一个单词的长度

https://www.nowcoder.com/practice/8c949ea5f36f422594b306a2300315da?tpId=37&tags=&title=&difficulty=&judgeStatus=&rp=1&sourceUrl=%2Fexam%2Foj%2Fta%3FtpId%3D37

```js
const rl = require("readline").createInterface({ input: process.stdin });
var iter = rl[Symbol.asyncIterator]();
const readline = async () => (await iter.next()).value;

void (async function () {
  // Write your code here
  while ((line = await readline())) {
    let tokens = line.split(" ");
    console.log(tokens[tokens.length - 1].length);
  }
})();
```

# HJ12 字符串反转

https://www.nowcoder.com/practice/e45e078701ab4e4cb49393ae30f1bb04?tpId=37&tags=&title=&difficulty=0&judgeStatus=0&rp=1&sourceUrl=%2Fexam%2Foj%2Fta%3FtpId%3D37

```js
const rl = require("readline").createInterface({ input: process.stdin });
var iter = rl[Symbol.asyncIterator]();
const readline = async () => (await iter.next()).value;

void (async function () {
  // Write your code here
  while ((line = await readline())) {
    let tokens = line.split("").reverse().join("");
    console.log(tokens);
  }
})();
```

# HJ13 句子逆序

https://www.nowcoder.com/practice/48b3cb4e3c694d9da5526e6255bb73c3?tpId=37&tags=&title=&difficulty=0&judgeStatus=0&rp=1&sourceUrl=%2Fexam%2Foj%2Fta%3FtpId%3D37

```js
const rl = require("readline").createInterface({ input: process.stdin });
var iter = rl[Symbol.asyncIterator]();
const readline = async () => (await iter.next()).value;

void (async function () {
  // Write your code here
  while ((line = await readline())) {
    let tokens = line.split(" ").reverse().join(" ");
    console.log(tokens);
  }
})();
```

# HJ14 字符串排序

https://www.nowcoder.com/practice/5af18ba2eb45443aa91a11e848aa6723?tpId=37&tags=&title=&difficulty=0&judgeStatus=0&rp=1&sourceUrl=%2Fexam%2Foj%2Fta%3FtpId%3D37

```js
// 这个我直接用sort ,应该还有那个获取codechatAt的方法
const rl = require("readline").createInterface({ input: process.stdin });
var iter = rl[Symbol.asyncIterator]();
const readline = async () => (await iter.next()).value;

void (async function () {
  let line = await readline();
  let newArr = [];
  for (let i = 0; i < line; i++) {
    newArr.push(await readline());
  }
  newArr.sort();
  // console.log(newArr.sort())
  for (let j = 0; j < newArr.length; j++) {
    console.log(newArr[j]);
  }
})();
```

# HJ15 求 int 型正整数在内存中存储时 1 的个数

https://www.nowcoder.com/practice/440f16e490a0404786865e99c6ad91c9?tpId=37&tags=&title=&difficulty=0&judgeStatus=0&rp=1&sourceUrl=%2Fexam%2Foj%2Fta%3FtpId%3D37

```js
const rl = require("readline").createInterface({ input: process.stdin });
var iter = rl[Symbol.asyncIterator]();
const readline = async () => (await iter.next()).value;

void (async function () {
    // Write your code here
    while ((line = await readline())) {
        let num = 0;
        let nums=Number(line).toString(2);
        for(let i in nums){
            if(+nums[i]==1){
                num++
            }
        }
        console.log(num);
    }
})();


```

# HJ16 购物单
https://www.nowcoder.com/practice/f9c6f980eeec43ef85be20755ddbeaf4?tpId=37&tags=&title=&difficulty=0&judgeStatus=0&rp=1&sourceUrl=%2Fexam%2Foj%2Fta%3FtpId%3D37
```js
// 这个得用背包问题解 但是现在不会 下次再说吧 先这样吧
```