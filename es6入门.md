	#es6基础入门
```javascript
// var a = [];
		// for(var i=0; i<10; i++){
		// 	a[i] = function(){
		// 		console.log(i);
		// 	}
		// }
		// a[3](); // 10


		// let 变量 
		// const 常量

		var a = [];
		for(let i=0; i<10; i++){
			a[i] = function(){
				console.log(i);
			}
		}
		a[3](); // 3

		// 匿名函数的写法(箭头函数)
		// funtion(a,b){console.log(a+b)}
		(a,b)=>console.log(a+b)

		// 对象扩展
		var test1 = {
			say:function(){
				console.log('es6');
			}
		}
		var test2 = {
			__proto__: test1
		}

		// 构造函数和继承
		class Preson(){

		}
		class Doctor extends Person(){

		}

		// Promise 异步函数

		let promise = new Promise(function(resolve,reject){
			console.log("Promise");
			resolve();
		});

		promise.then(function(){
			console.log('Resolved.');
		},function(){
			console.log('reject');
		});
		console.log('Hi');
    ```
