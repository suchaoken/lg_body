<template>
    <div class="navigation">
        <div @click="toPageOne">PageOne</div>
        <div @click="toPageTwo">PageTwo</div>
        <div @click="toPageThree">PageThree</div>
    </div>
</template>
<script>
import { useWebsocket } from "../hooks";
export default {
    data() {
        return {
            ws: "111",
        };
    },
    mounted() {
        this.ws = useWebsocket(handleMessage);
        let that = this;
        function handleMessage(e) {
            let data = JSON.parse(e.data);
            if (data.message == "ipad1") {
                that.$router.push("/");
            } else if (data.message == "ipad2") {
                that.$router.push("/pagetwo");
            } else if (data.message == "ipad3") {
                that.$router.push("/pagethree");
            }
        }
    },
    methods: {
        toPageOne() {
            this.ws.send(
                JSON.stringify({
                    message: "body1",
                    DateTime: new Date().getTime(),
                })
            );
            this.$router.push("/");
        },
        toPageTwo() {
            this.ws.send(
                JSON.stringify({
                    message: "body2",
                    DateTime: new Date().getTime(),
                })
            );
            this.$router.push("/pagetwo");
        },
        toPageThree() {
            this.ws.send(
                JSON.stringify({
                    message: "body3",
                    DateTime: new Date().getTime(),
                })
            );
            this.$router.push("/pagethree");
        },
    },
};
</script>
<style scoped>
.navigation {
    height: 400px;
    width: 150px;
    background-color: rgb(94, 121, 136);
}
</style>