###call apply  bind
###共同点：
 >1.改变this指向   （this：当前调用这个方法或属性，前面是谁就是谁）

 >>**call 和 apply 的共同点：**
   1.都是让当前方法执行，并且让当前这个方法中this变为第一个参数
   2.都可以传递多个参数的   

###不同点：

​    1.call：第一个参数改变this指向  以后的参数都是传递的实参
​    2.apply：第一个参数改变this指向  后边可以传递一个数组

```javas
<script>
	function B() {
            this.a = 2000;
        }
   
   		B.prototype.getX = function (x,y,z) {
        console.log(this); //obj3:{a:"哈哈哈哈哈"}
        console.log(this.a);{a:"哈哈哈哈哈"}
        console.log(x,y,z); //20 20 40
    	}
    
    	var b = new B();
        var obj3 = {a:"哈哈哈哈哈"};
        b.getX.call(obj3,20,20,40,100);
        b.getX.apply(obj3,[20,20,40,100]);
</script>
```

3.bind:也是用来改变this指向的，不过不是立即改变，什么时候调用什么时候才改变

```javascript
<script>
    function A(){
        this.age = 100;
    }

    A.prototype.getY = function (x,y){
        console.log(this);  //obj  {name:"HAHA"}
        console.log(this.age,x,y); // undefined 100  200
    }

    var a = new A();
    var obj = {name:"HAHA"};

    var temBind = a.getY.bind(obj,100,200);
    //这里的返回值就是要执行的那个函数
    console.log(temBind);  //function(x,y){}
    // 调用去改变this指向并且传递参数
    temBind();
<script>
```

