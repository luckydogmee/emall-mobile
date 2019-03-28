<template>
    <div class="cart-container">
        <img :src="cartSrc" alt="" >
    </div>
</template>

<script>
export default {
    name:'yCart',
    props:{
        disabled:{
            type: Boolean,
            default: false
        }
    },
    computed:{
        cartSrc(){
            return this.disabled ? require('@/assets/icon/cart-disabled.png') : require('@/assets/icon/cart.png')
        }
    },
    methods:{
        
    }
}
</script>

<style lang="less" src="./index.less" scoped></style>
