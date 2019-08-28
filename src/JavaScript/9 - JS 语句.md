# JS 语句


### 分类

![普通语句](../imgs/statement1.png)
![声明型语句](../imgs/statement2.jpeg)


- 语句块：大括号里的语句
- 空语句：没有实际作用，语言设计完备性角度考虑
- if 语句
- switch 语句，推荐使用 if...else 代替

##### 循环语句
- while; do while: 很少使用
```js
let a = 100
while(a--) {
    console.log("*");
}
let a = 101;
do {
    console.log(a);
} while(a < 100)

```
- for
```js

for(i = 0; i < 100; i++)
    console.log(i);

for(var i = 0; i < 100; i++)
    console.log(i);

for(let i = 0; i < 100; i++)
    console.log(i);

var j = 0;
for(const i = 0; j < 100; j++)
    console.log(i);
```
- for in : 循环枚举对象的属性，很少使用

- for of ; for await of 重点学习
```js
for(let e of [1, 2, 3, 4, 5])
    console.log(e);
```

其背后是 `iterator` 机制
```js
let o = {  
    [Symbol.iterator]:() => ({
        _value: 0,
        next(){
            if(this._value == 10)
                return {
                    done: true
                }
            else return {
                value: this._value++,
                done: false
            };
        }
    })
}
for(let e of o)
    console.log(e);
```
实际代码中一般使用 `generator function`
```js
function* foo(){
    yield 0;
    yield 1;
    yield 2;
    yield 3;
}
for(let e of foo())
    console.log(e);
````

**新知识点学习**
异步的 `for of`
```js
// 每秒打印一个数字
function sleep(duration) {
    return new Promise(function(resolve, reject) {
        setTimeout(resolve,duration);
    })
}
async function* foo(){
    i = 0;
    while(true) {
        await sleep(1000);
        yield i++;
    }
        
}
for await(let e of foo())
    console.log(e);
```


- return 语句

- break continue

- with: 不推荐使用

- try throw: 可在 catch 中再次抛出异常，多用于标识异常代码段、提示 

- debugger

#### 声明型语句
- var : 不推荐使用

- let const 

- class

- 函数声明

```js

function foo(){

}

function* foo(){
    yield 1;
    yield 2;
    yield 3;
}

async function foo(){
    await sleep(3000);
    
}

async function* foo(){
    await sleep(3000);
    yield 1;
}
```