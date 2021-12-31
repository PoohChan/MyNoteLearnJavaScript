1 变量

	使用 let,const 去命名变量。var老旧的方式，不推荐使用
	
1.1 数据类型

基本：number, bigint, string, boolean, undefined, null, symbol
复杂：object

number 
	NaN Infinity
	1/0 = Infinity
	let a = 1;

bigint 
	正负2的53次方减一之外的整数
	let a = 1n;

string
	let str = "hello"
	let str2 = 'hello'
	let str3 = `hello ${str}`
	
boolean
	let d = true;
	let e = false;
null
	let c = null;
	typeof c 是Object, 这是兼容的错误
undefined
	let a;

typeof 运算符
	typeof a;
	typeof(a);

1.2 交互

	alert 弹窗
	prompt 第一显示，第二个输入框提示是可选。返回字符串
	confirm 确定或取消。返回boolean

1.3 类型转换
	
	let n = true;
	n = String(n);
	
	let m = '332';
	m = Number(m);
	不是有效数字会转为 NaN
	undefined -> NaN
	null -> 0
	true/false -> 1/0
	string 
	
	let x = 1;
	Boolean(x);
	null/undefined/0/''/NaN -> false

1.4 运算符

1.5 比较
	普通相等==
		字符串比较，逐位比较
		不同类型比较，转为数字再比较
		null 和 undefined 相等比较时会有自己的比较规则，只能和自己相等
	严格相等===
		先比较类型，再比较内容
		=== !==
	null == undefined   true
	null === undefined  false
	
	null > 0 	false
	null == 0 	false
	null >= 0 	true
	
	undefined > 0	false
	undefined < 0	false
	undefined == 0	false
	
2 if条件分支
	三目运算符

2.1 逻辑运算符
	与或非
	
2.2 合并空值运算符 ??
	a ?? b 如果a是 null 或者 undefined 则是b
	可以连续使用 a ?? b ?? c ?? d
	?? 优先级低为5，必要时加括号

2.3 循环
	for
	do.while
	while
	多层循环跳出使用标签
	
2.4 switch

2.5 函数初步
	函数对外部变量拥有全部修改权限
	同名内部变量会遮蔽外部变量
	参数不传入就是用undefined
	参数默认值可以是复杂计算，可以是一个函数计算值
	
2.6 函数表达式
	函数是个特殊的值，赋值
	
	函数声明，函数表达式
	function sayHi(name) {
		alert( `Hello, ${name}` );
	}
	
	let sayHi = function(name) {  // (*) no magic any more
		alert( `Hello, ${name}` );
	};
	
	箭头函数，一行不用显示return 多行花括号return
	
	
*2.7 mochi测试

3.0 object

	//1定义
	let user = new Object();
	let user = {};
	delete user.hello
	
	//2中括号获取定义，
	let key = a + b + c;
	user[key] = "hello"
	
	//3判断key是否在Object中, 比===undefined更全，因为定义一个值为undefined的变量就傻眼了，尽管这种是不合理的定义方式
	key in user		//true
	
	//4loop
	for(key in user){
		user[key]
	}
	for(let key in user){
		user[key]
	}
	
3.1 object copy

	//增量式复制
	Object.assign(dest, [src1, src2, src3...])
	
*3.2 garbage collection 垃圾回收
	reachability

3.3 object methods
	在函数中使用this关键字获取object中的值
	this没有绑定，被赋予谁就是谁
	
3.4 constructor
	1. create a new empty object to this.
	2. function body executes
	3. return this
	
	构造函数中命名变量使用this. 命名

3.5 ?. 可选链
	多层嵌套，如果不存在值返回undefined
	
	obj?.prop
	obj?.[prop]
	obj.method?.()
	
3.6 symbol
	//1和string作为object的唯二键值类型
	
	//2参数只作为标签不实际标志symbol
	let id = Symbol("id");
	user[id] = "123"
	
	//作为隐藏属性无侵入变成实体属性
	//3 loop无法看到symbol属性
	
	//4 创建全局symbol, 无则创建有则覆盖，起名相同的话是完全一样的
	let hello = Symbol.for("hello");
	let helloAgain = Symbol.for("hello");
	hello === helloAgain
	
	//5 根据全局symbol找到名称，本地symbol不行
	let name = Symbol.keyFor(hello);
	
	//6Reflect.ownKeys(obj) 可以看到实体里的key
	
	//7 js自带很多global symbol
	
	//8 symbol 可以被函数赋值

3.7 object to primitive conversion

	3种暗示转换，在需要时转换为原始类型。内置symbol [toPrimitive] 被赋值为函数
	number ：数学运算
	string ： 需要字符串时
	default
	
	obj[Symbol.toPrimitive](hint)
	

4

	

	
	