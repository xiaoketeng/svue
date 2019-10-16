<template>
    <div>
        <label v-if="label">{{label}}</label>
        <!-- 插槽 -->
        <slot></slot>
        <!-- 校验错误信息 -->
        <p v-if="errorMessage" class="error">{{errorMessage}}</p>
        <slot name="foo"></slot>
    </div>
</template>
<script>
export default {
    props:['label','prop'],
    data(){
        return{
            errorMessage:''
        }
    }
}
</script>
<style>
    .error{
        color:red;
    }
</style>