## 数据类型：
      原始类型：number/string/boolean/null/undefined/symbol
      对象类型：object（包括，数组、对象、函数等对象）
## 新增类型：
      let 变量: 类型1 | 类型2 | 类型3 .... = 初始值
## 类型别名：
      type NewType = string | number
      let a: NewType = 1
      let b: NewType = '1'
## 数组类型：
      // 写法1：
      let 变量: 类型[] = [值1，...]:
      let numbers: number[] = [1, 3, 5] 
      //  numbers必须是数组，每个元素都必须是数字
      // 写法2：
      let 变量: Array<类型> = [值1，...]
      let strings: Array<string> = ['a', 'b', 'c'] 
      //  strings必须是数组，每个元素都必须是字符串
## 函数：
      // 普通函数
      function 函数名(形参1： 类型=默认值， 形参2：类型=默认值,...): 返回值类型 { }
      // 声明式实际写法:
      function add(num1: number, num2: number): number {
        return num1 + num2
      }

      // 箭头函数
      const 函数名（形参1： 类型=默认值， 形参2：类型=默认值, ...):返回值类型 => { }
      const add2 = (a: number =100, b: number = 100): number =>{
         return a + b
       }
       // 注意： 箭头函数的返回值类型要写在参数小括号的后面
      add（1,'1') // 报错
## 统一定义函数格式：
       const add2 = (a: number =100, b: number = 100): number => {
           return a + b
         }

       function add1 (a:number = 100 , b: number = 200): number {
           return a + b
         }
       // 这里的 add1 和 add2 的参数类型和返回值一致，
       // 那么就可以统一定义一个函数类型
       type Fn = (n1:number,n2:number) => number 
       const add3 : Fn = (a,b)=>{return a+b }
       // 这样书写起来就简单多啦
## 函数返回值类型void：
     function greet(name: string): void {  console.log('Hello', name)  //}
        可以用到void 有以下几种情况
            1.函数没写return
            2.只写了 return， 没有具体的返回值
            3.return 的是 undefined
## 对象类型-单独使用
       格式：
        方法有两种写法： 普通函数 和 箭头函数
        const 对象名: {
          属性名1：类型1，
          属性名2?：类型2，
          方法名1(形参1: 类型1，形参2: 类型2)： 返回值类型,
          方法名2:(形参1: 类型1，形参2: 类型2) => 返回值类型
        } = { 属性名1: 值1，属性名2：值2  }

## 对象类型-类型别名
       // 创建类型别名
       type Person = {
         name: string，
         age: number
         sayHi(): void
       }

       // 使用类型别名作为对象的类型：
       let person: Person = {
         name: '小花',
         age: 18
         sayHi() {}
       }

## 接口
      当一个对象类型被多次使用时，有如下两种方式来来描述对象的类型，以达到复用的目的：
      类型别名，type      接口，interface
### 语法：
      interface 接口名  {属性1: 类型1, 属性2: 类型2}
      // 这里用 interface 关键字来声明接口
      interface IGoodItem  {
      	// 接口名称(比如，此处的 IPerson)，可以是任意合法的变量名称，推荐以 `I` 开头
         name: string, price: number, func: ()=>string
      }

      // 声明接口后，直接使用接口名称作为变量的类型
      const good1: IGoodItem = {
         name: '手表',
         price: 200,
         func: function() {
             return '看时间'
         }
      }
      const good2: IGoodItem = {
          name: '手机',
          price: 2000,
          func: function() {
              return '打电话'
          }
      }

## 接口和类型 的区别
     interface（接口）和 type（类型别名）的对比：
      相同点：都可以给对象指定类型
      不同点:
        接口，只能为对象指定类型。它可以继承。
        类型别名，不仅可以为对象指定类型，实际上可以为任意类型指定别名

      先有的 interface，后有的 type,推荐使用 type

     // 接口的写法-------------
     interface IPerson {
     	name: string,
     	age: number
     }

     const user1：IPerson = {
	     name: 'a',
     	age: 20
     }

     // type的写法-------------
     type Person  = {
     	name: string,
     	age: number
     }
     const user2：Person = {
	     name: 'b',
	     age: 20
     }

#### any 类型
     any: 任意的。当类型设置为 any 时，就取消了类型的限制。














