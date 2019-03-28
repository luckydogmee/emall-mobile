<template>
    <div class="number-selector" :style="{width,height}">
        <div class="number-decrease" @click.stop.prevent="decrease">-</div>
        <input class="number-input" maxlength="8" v-model.number="number" />
        <div class="number-increase" @click.stop.prevent="increase">+</div>
    </div>
</template>

<script>
import numeral from 'numeral'
export default {
    name:'Number',
    props:{
        height: {
            type: String,
            default: '5.867vw'
        },
        width: {
            type: String,
            default: '25.333vw'
        },
        step: {
            type: Number,
            default: 1
        },
        value: {
            type: Number,
            default: 0
        },
        max: {
            type: Number,
            default:999999999
        },
        min: {
            type: Number,
            default: 0
        },
        disabled:{
            type: Boolean,
            default: false
        }
    },
    data(){
        return {
            number: 0
        }
    },
    created(){
        this.number = this.value
    },
    watch:{
        number(newVal, old){
            if(newVal !== ''){
                if(this.min !== 'undefined' && this.number<this.min){
                    this.number = this.min
                }
                if(this.max !== 'undefined' && this.number > this.max){
                    this.number = this.max
                }
            }else{
                this.number = this.min
            }
            this.$emit('input',this.number)
        },
        value(newVal){
            this.number = newVal
            this.$emit('on-change',newVal)
        }
    },
    methods:{
        decrease(){
            if(this.number > this.step && this.number){
                this.number = this.number - this.step
            }
        },
        increase(){
            if(this.number <this.max && this.max - this.number >= this.step){
                this.number = this.number + this.step
            }
        }
    }
}
</script>
<style lang="less" src="./index.less" scoped></style>
