<!-- model 模型 -->
<template>
    <div class="container">

        <div class="functions">
            <load-model></load-model>
        </div>
        <div class="functions">
            <load3-d-tiles></load3-d-tiles>

        </div>
        <div class="functions">
            <load3-d-tiles-bim></load3-d-tiles-bim>
        </div>

    </div>
</template>

<script>
    // 导入自己封装的轮播图子组件
    import {mapActions, mapState} from 'vuex'

    import LoadModel from '../subcomponents/LoadModel.vue'
    import Load3DTiles from '../subcomponents/Load3DTiles.vue'
    import Load3DTilesBim from '../subcomponents/Load3DTilesBim.vue'
    export default {
        data() {
            return {};
        },
        computed: {
            ...mapState(['tabPaneShowState']),

        },
        created() {
            // 选择显示

        },
        methods: {
            async getlunbotu() {
                // 获取轮播图的方法
                const {data} = await this.$http.get("/getlunbo");
                if (data.status === 200) this.lunbotu = data.result;
            }
        },
        components: {
            // 注册子组件
            LoadModel,
            Load3DTiles,
            Load3DTilesBim

        }
    };
</script>

<style lang="scss" scoped>
    .layer {
        background-color: #f6f6f6;

        border-width: 0.001px;
        border-color: #e2e2e2;

        /*border: solid;*/
    }

    .container{
        display: flex;
        height: 78px;
        .functions {
            margin-left:3px;
            /*border-style:solid;*/
            border-width:1px;
            /*font-size: 20px;*/
            text-align: center;
        }

    }
    .exist {

    }

    .not-exist {
        display: none;
    }


</style>
