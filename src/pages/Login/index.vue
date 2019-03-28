<template>
    <div>
        <div class="logo">logo</div>
        <div>
            <div class="form-control" :class="{focus: focusItem === 'account'}">
                <label for="account">
                    <img src="@/assets/icon/account.png" alt="" srcset="">
                </label>
                <input type="text" name="account" ref="account" placeholder="输入账号" @focus="focusItem = 'account'" v-model="account">
            </div>
            <div class="form-control" :class="{focus: focusItem === 'password'}">
                <label for="password">
                    <img src="@/assets/icon/password.png" alt="" srcset="">
                </label>
                <input type="text" name="password" ref="password" placeholder="输入密码" @focus="focusItem = 'password'" v-model="password">
            </div>
            <div class="form-control" :class="{focus: focusItem === 'verification'}">
                <label for="verification">
                    <img src="@/assets/icon/verification.png" alt="" srcset="">
                </label>
                <input type="text" name="verification" ref="verification" placeholder="输入验证码" @focus="focusItem = 'verification'" v-model="verification">
                <img class="verification" src="@/assets/icon/verification.png"/>
            </div>
            <div class="error-info">
                <ul>
                    <li v-for="item in errors" :key="item">{{item}}</li>
                </ul>
            </div>
            <yButton class="login-btn" borderRadius="44px" type="primary" size="large" @click="login" :disabled="disable">登 录</yButton>
            <yButton >查看详情</yButton>
            <yButton type="normal" >查看详情</yButton>
            <yButton type="primary">查看详情</yButton>
            <yNumber v-model="value"></yNumber>
            <yCart />
        </div>    
    </div>
</template>

<script>
import yButton from '@/baseComponents/yButton'
import yNumber from '@/baseComponents/yNumber'
import yCart from '@/baseComponents/yCart'
export default {
    name:'login',
    data(){
        return {
            account:'',
            password:'',
            verification:'',
            focusItem:'',
            errors:[],
            value:2
        }
    },
    mounted(){
        this.$api.get('baidu.com')
        .then((res)=>{
            console.log(res)
        }).catch((err)=>{
            console.log(err)
        })
    },
    components:{
        yButton,
        yNumber,
        yCart
    },
    computed:{
        disable(){
            if(this.account&&this.password&&this.verification && this.errors.length===0){
                return false
            }
            return true
        }
    },
    watch: {
        value(newVal,old){
            console.log(newVal,old)
        }
    },
    methods:{
        login(){
            this.$router.push({'name':'home'})
        },
    }
}
</script>

<style lang="less" scoped src="./index.less"></style>
