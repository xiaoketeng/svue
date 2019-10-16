<template>
   <div>
       <h3>KForm表单</h3>
       <hr>
       <k-form-item label="用户名" prop="username">
           <k-input :value="model.username" type="text" @input="model.username=$event"></k-input>
       </k-form-item>
    
      <k-form-item label="密码" prop="password">
           <k-input :value="model.password" type="password" @input="model.password=$event"></k-input>
           <template v-slot:foo>foo content</template>
      </k-form-item>

      <k-form-item>
           <el-button type="primary" @click="submitForm('loginForm')">提交</el-button>
      </k-form-item>


       <h3>Element表单</h3>
       <hr>
       <el-form :v-model="model" :rules="rules" ref="loginForm">
           <el-form-item label="用户名" prop="username">
               <el-input v-model="model.username" autocomplete="off"></el-input>
           </el-form-item>
           <el-form-item label="确认密码" prop="password">
               <el-input type="password" v-model="model.password" autocomplete="off"></el-input>
           </el-form-item>
           <el-form-item>
               <el-button type="primary" @click="submitForm('KForm')">提交</el-button>
           </el-form-item>
       </el-form>
   </div>
</template>
<script>
import KInput from './Kinput.vue';
import KFormItem from './KFormItem.vue';
export default{
    data(){
        return{
           //数据模型
           model:{username:"tom",password:""}, 
           //校验规则
           rules:{
               username:[{required:true,message:"请输入用户名"}],
               password:[{required:true,message:"请输入密码"}]
           }
        }
    },
    components:{
        KInput,
        KFormItem
    },
    methods:{
        submitForm(form){
            //表单全局校验
            this.$refs[form].validate(valid=>{
                if(valid){
                    alert("请求登录!");
                }else{
                    alert("校验失败!");
                }
            });
        }
    }
}
</script>
<style scoped>
    .el-form{
        display: inline-block;
        vertical-align: top;
    }
</style>