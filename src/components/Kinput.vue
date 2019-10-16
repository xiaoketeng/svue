<template>
<!-- 双向数据绑定的实现 -->
    <div>
        <input :type="type" :value="value" @input="onInput">
    </div>
</template>

<script>
export default {
    props:{
        type:{
            type:String,
            default:'text'
        },
        value:{
            type:String,
            default:''
        }
    },
    methods:{
        onInput(e){
            //通知父级发生了input事件
            this.$emit('input',e.target.value);
        }
    }
}
</script>

<style>
    
</style>