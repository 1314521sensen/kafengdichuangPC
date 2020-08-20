<template>
    <div>
        <headnavigationmap />
        <userOperationNav />
    </div>
</template>
<script>
import headnavigationmap from "@/components/public/header/Navigationmap.vue"
import userOperationNav from "@/components/public/header/userOperationNav.vue"
    export default {
        data(){
            return {

            }
        },
        components:{
            headnavigationmap,
            userOperationNav
        }
    }
</script>
<style lang="less">

</style>