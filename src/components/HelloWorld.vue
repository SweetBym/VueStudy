<template>
  <div class="hello">
    <h1>Vue官网文档学习</h1>
    <h2>Vue一些常用指令的学习与使用</h2>
    <div>
      <div>computed计算属性的应用</div>
      <p>利用computed属性对msg中的信息进行反转： {{msg}}</p>
      <p>反转后的信息: {{reverseMsg}}</p>
    </div>
     <br/>
    <div >
      <div><span style = "color: red;">侦听器watch属性的应用：</span> 当数据在变化时，并且需要执行异步操作或者开销较大的操作时，使用该属性较为合适</div>
      <div>
         <span>
           今天是星期几：<input   v-model = "question">
         </span>
        <span>{{answer}}</span>
      </div>
    </div>
    <br/>

    <div>
      <div style="color: red;">当你想某要动态的改变某个元素的样式时，我们可以通过 v-bind:class 指令实现</div>
      <br/>
      <span>第一种方法，直接将绑定的数据以内联的方式定义在模板中</span>
      <div  v-bind:class = "{apple: isGreen, bananar: isYellor}" @click = "changeCol">点击我，我会改变颜色哦</div> <br/>
      <span>第二种方法：不以内敛的方式绑定样式 </span>
      <div  :class = "alsoChangecolor" >我是第二种方法 </div><br/>
      <p>也可以通过 v-bind: style 来实现对样式的改变</p>
      <div  v-bind:style = "thirdChange">我是利用v-bind:style 改变的哦</div>
    </div>

    <div>
      <div style="color: red;">v-for的应用</div> <br/>
      <span>v-for 对数组的遍历</span>
      <div>
        <ul v-for = "(item,index) in newArr">
          <li> {{index }} ： {{item.fruit}}</li>
        </ul>
      </div>
      <hr/>

      <div style="color: red;"> v-for对对象的遍历</div>
      <div>
        <ul v-for = "(item, key, index ) in newArr1">
          <li>{{index}}. {{key}} : {{ item}}</li>

        </ul>
      </div>
    </div>




  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'HelloWorld',
      question: '',
      answer: '你猜一猜',
      isGreen: false,
      isYellor: true,
      alsoChangecolor: {
        pear: true,
        lemon: true
      },
      thirdChange: {
          fontSize: '20px',
        color: '#aaffee'
      },
      newArr: [
        {fruit: 'mango '},
        {fruit: 'strawberry'}
      ],

      newArr1: {
        age: 20,
        name: 'Tom',
        hobby: 'basketball'
      }


    }
  },

  //计算属性的应用
  computed: {
    reverseMsg: function () {
        return this.msg.split('').reverse().join('')
    }

  },

  // wacth属性的应用
  watch : {
    //如果上面被绑定的question发生变化时，即你在输入框输入数据时，下面的函数将会立即执行
    question: function (oldqQuestions,newQuestions) {
        this.answer = "拿出手机出来自己看看吧"
    }

  },


  methods: {
    changeCol(){
        this.isGreen = true;
        this.isYellor =  false;
    }


  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1 {
    font-weight: normal;
  }
  .apple{
    color: blue;
  }
  .bananar{
    border: 1px solid black;
  }

  .pear{
    color: purple;
  }
  .lemon{
    border: 1px solid brown;
  }

</style>
