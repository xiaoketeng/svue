<template>
  <div class="hello">
    <!-- 条件 -->
    <span :title="title" v-if="title">{{title}}</span>
    
    <!-- 用户输入 -->
    <div>
      <input type="text" v-model="text">
      <button @click="addGood">添加商品</button>
    </div>
 
  <!-- 循环 -->
  <ul>
    <li v-for="good in goods" :key="good.id">
      <span>{{good.text}}</span>&nbsp;&nbsp;     
      <span>￥{{good.price}}</span>
      <button @click="addCart(good)">加购物车</button>
    </li>
  </ul>
  <!-- 购物车 -->
  <cart title="abc" ref="cart" @addCart="onAddCart()"></cart>
  </div>
</template>

<script>
import Cart from './Cart.vue';
export default {
  name: 'HelloWorld',
  data:function(){
    return {
      text:'dddd',
      title:'',
      goods:[
        {
          id:1,text:'web全栈架构师',price:'1199'
        },
        {
          id:2,text:'web全栈架构师2',price:'2199'
        }
      ]
    }
  },
  created(){
    setTimeout(()=>{
      this.title = '开课吧购物车'
    },1000);
  },
  components:{
    Cart
  },
  methods:{
    onAddCart(){
      console.log('lalala');
    },
    addCart(good){
      //添加购物车
      // this.$refs.cart.addCart(good);
      //派发事件
      this.$bus.$emit('addCart',good);
    },
    addGood(){
      if(this.text){
        this.goods.push({
          id:this.goods.length+1,
          text:this.text,
          price:6999
        });
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

a {
  color: #42b983;
}
</style>
