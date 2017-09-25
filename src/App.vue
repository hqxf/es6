<template>
  <div id="app">
    hq
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  methods:{
    //es和js的关系
    relationship: () => {
      //console.log("ECMAScript 和 JavaScript 的关系是，前者是后者的规格，后者是前者的一种实现（另外的 ECMAScript 方言还有 Jscript 和 ActionScript）。日常场合，这两个词是可以互换的。");
    },
    //let和const声明
    letAndConstState: () => {
      for (let i = 0; i < 3; i++) {
        let i = 'abc';  //for特殊 可以重新定义i
        //console.log(i);
      };
      //1.不存在变量提升
      //2.暂时性死区
      //3.不允许重复声明
      //2.
      //2.
    },
    //Destructuring 解构
    destructuring: () => {
      let [x=1] = [undefined];
      //console.log(x);
      let [y=1] = [null];
      //console.log(y);
      let {foo,bar} = {foo:"aaa", bar: "bbb"}
      //console.log(foo);
      let {a:bza} = {a: "aaa", b: "bbb"};
      //console.log(bza);
      let obj = {
        p:[
          'hello',
          {n:'world'}
        ]
      }
      let {p,p:[m,{n}]} = obj;  // p:[m,{n}] 这里p是模式
      //console.log(p,n,m);
      let h;
      ({h} = {h:8}); //一个变量解构时候,h会被当做代码块,会报错,加()立即执行
      //console.log(h);
      function move({x=0,y=0}={x,y}) { 
        console.log([x,y]);
      };
      /*move({x:3,y:8});
      move({x:3});
      move({});*/
      function move1({x,y}={x:0,y:0}) {  //参数给一个默认的对象
        console.log([x,y]);
      }
      /*move1({x:3,y:8});
      move1({x:3});
      move1();*/
    },
    //String expansion 字符串扩展
    stringExpansion: () => {
      //字符串遍历
      for(var i of "adfasf") {
        //console.log(i);
      }
    },
    //function 函数
    func: () => {
      function Point(x=0,y=0) {
        //默认参数已经有默认声明,不能再次用let/const声明
        this.x = x;
        this.y = y;
      }
      var p = new Point();
      //console.log(p);
      function add(...rest) {
        var num = 0;
        for(var i of rest) {
          num += i
        }
        //console.log(num);
      }
      add(1,2,3,4);
      //console.log(add.name);  //name属性
      //console.log(add.length); //length属性  默认或者rest都不计算到length里面
      let add1 = (a,b) => {console.log(a+b);}
      //add1(1,2);

      //箭头函数
        //1.函数体内的this对象,就是定义时所在的对象,而不是使用时所在的对象(this指向是固定的,不能改变的)
        //2.不可以当做构造函数使用,也就是说不可以使用new命令
        //3.不可以使用arguments,如果要使用参数,可以用rest代替
        //4.    不可以使用yield命令,该对象在函数体内不存在,否则会抛出一个错误

        window.id = 21;
        function fun() {
          setTimeout(() => {
            console.log(this.id);
          },1000)
        }
        //fun.call({id:23});

        function fib(n) {
          if(n<=1) return 1;
          return fib(n-1) +fib(n-2);
        }
        console.log(fib(6));

        function fib1(n, a=1, b=1) {
          if(n<=1) {
            return b;
          }
          return fib1(n-1,b,b+a);
        }
        console.log(fib1(6));
    }
  },
  mounted(){
    this.relationship();
    this.letAndConstState();
    this.destructuring();
    this.stringExpansion();
    this.func();
  }
}
</script>

<style>
  @import './assets/base.less';
</style>
