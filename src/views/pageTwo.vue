<template>
    <div class="pageTwo">
        <!-- <navigation></navigation> -->
        <div class="title">pageTwo</div>
        <div id="main" style="width: 600px; height: 400px;"></div>
    </div>
</template>
<script>
import navigation from "./navigation.vue";
import lgMap from "@/assets/lg.json";
export default {
    data() {
        return {
            option: {
                label: {
                    // name:JDNAME,
                    show: true, //是否显示市
                    textStyle: {
                        color: "white", //文字颜色
                        fontSize: 10, //文字大小
                    },
                },
                series: [
                    {
                        type: "map",
                        map: "lgMap1",
                        label: {
                            show: true,
                        },

                        // 自定义名称映射
                    },
                ],
            },
        };
    },
    components: {
        navigation
    },
    created() {},
    methods: {},
    mounted() {
        let myChart = this.$echarts.init(document.getElementById("main"));
        this.$echarts.registerMap("lgMap1", lgMap);
        myChart.setOption(this.option);
        console.log(lgMap);
    },  
};
</script>
<style scoped>

.pageTwo {
    height: 600px;
    width: 980px;
    position: relative;
    background-color: rgb(226, 235, 210);
}
#main{
    position: absolute;
    left: 50%;
    top: 50%;
    transform:translate(-50%,-50%);
    background-color: rgb(194, 97, 97);
}
.navigation{
    position: absolute;
    top: 30px;
    left: 0px;
    float: left;

    
}
.title{
    position: absolute;
    left: 50%;
    transform: translate(-50%);
}
</style>