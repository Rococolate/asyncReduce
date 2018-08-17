# asyncReduce
Combine Promise and Array.prototype.reduce into  asyncReduce

## Use

```js
const asyncReduce = require('asyncReduce');

const list = [1,2,3,4,5];

async function sleep(time){
  await new Promise((resolve) => {
    setTimeout(resolve, time);
  });
}

asyncReduce(list, async (pre,cur,index,array)=>{
  const totle = pre + cur;
  console.log(totle);
  await sleep(1000);
  return totle; 
},0)
.then(value => console.log(value))
.catch(err=> console.log(err));

```


output:

```js
1
(after 1000ms)
3
(after 1000ms)
6
(after 1000ms)
10
(after 1000ms)
15
(after 1000ms)
15
```