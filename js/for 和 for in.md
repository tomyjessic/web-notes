###for循环  一般我们用来遍历数组和类数组

###for in 循环  一般用来遍历对象  不建议用来循环遍历数组
原因：1.会把下标变为字符串
      2.for in循环会把私有属性或方法和公有属性或方法都遍历出来
```
    <script>
        var arr= new Array(110,200,3,400,300);
        // 公有属性
        Array.prototype.getX= function () {
    
        }
        Array.prototype.getY =function () {
    
        }
        私有属性
        arr.hello=110;
        arr.nihao=200;
    
        for (var i=0;i<arr.length;i++){
             console.log(i, arr[i]); //0,1,2,3,4  110,200,3,400,300
             console.log(typeof i,typeof arr[i]); // 均为Number 类型
         }
        for (var key in arr){
            console.log(key,arr[key]);//0,1,2,3,4   110,200,3,400,300,hello 110,nihao200,getX f(){},getY f(){}
            console.log(typeof key, typeof arr[key]);//7个string Number,2个string function
        }
    </script>
```