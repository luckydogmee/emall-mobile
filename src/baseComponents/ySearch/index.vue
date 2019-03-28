<template>
    <div>
        <div v-if="!panelStatus" class="search-min-panel" :style="currStyle" @click.native="handePanel">
            <div class="search-icon">
                <img src="./images/search.png" alt="">
            </div>
            <input type="text" :placeholder="placeHolder" readonly>
        </div>
        <div v-if="panelStatus" class="search-panel">
            <div class="search-input">
                <div class="search-icon">
                    <img src="./images/search.png" alt="">
                </div>
                <input type="text" :placeholder="placeHolder">
                <div class="search-cancel" @click="handePanel">取消</div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name:'ySearch',
    props:{
        showPanel:{
            type: Boolean,
            default: false
        },
        placeHolder:{
            type: String,
            default: '输入商品名/拼音/生产厂家/货号'
        },
        styles:{
            type: Object,
            default: ()=>{}
        }
    },
    created(){
        this.panelStatus = this.showPanel
    },
    computed:{
        currStyle(){
            return Object.assign({background:'#f4f4f4'},this.styles)
        }
    },
    methods:{
        handePanel(){
            this.panelStatus = !this.panelStatus
        }
    }
}
</script>

<style lang="less" scoped>
    .search-min-panel,.search-input{
        height:56px;
        width: 690px;
        border-radius: 28px;
        margin: 0 auto;
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: left;
        .search-icon{
            height:100%;
            width: 60px;
            display: flex;
            flex-direction: row;
            justify-content: center;
            align-items: center;
            img{
                height: 24px;
                width: 24px;
            }
        }
        input{
            flex: 1;
            background:rgba(0,0,0,0);
            border: none;
            display:inline-block;
            font-size: 26px;
            height:100%;
        }
    }
    
    
</style>
