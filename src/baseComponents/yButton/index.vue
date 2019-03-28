<template>
    <button :class="[type,size]" :style="{borderRadius:borderRadius}" @click="handleClick">
        <slot></slot>
    </button>
</template>

<script>
export default {
    name:'Button',
    props:{
        type:{
            type:String,
            default:'default'
        },
        size:{
            type:String,
            default:'middle'
        },
        borderRadius:{
            type:String,
            default:'3.733vw'
        }
    },
    mounted(){
        
    },
    methods:{
        handleClick(){
            this.$emit('click')
        }
    }
}
</script>

<style lang="less" src="./index.less" scoped></style>
