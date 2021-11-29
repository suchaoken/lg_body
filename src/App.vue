<template>
    <div>
        <navigation></navigation>
        <router-view />
    </div>
</template>

<style lang="scss">
</style>
<script>
import navigation from "./views/navigation.vue";

export default {
    mounted() {
        console.log(process.env.VUE_APP_BASE_URL);
    },
      components: {
        navigation,
    },
};
</script>
<style scoped>
/* div{
    position: relative;
} */
.navigation {
    z-index: 999;
    position: absolute;
    top: 30px;
    left: 20px;
    float: left;
}
</style>