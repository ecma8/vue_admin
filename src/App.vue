<template>
    <div id='app'>
        <router-view></router-view>
        <Loading v-if="$store.state.isLoading"></Loading>
    </div>
</template>
<script>
    import {mapGetters,mapActions} from 'vuex'
    import Loading from './components/Loading/Loading.vue'
    export default{
        data(){
            return {

            }
        },
        computed: {
//            ...mapGetters(['isLoading'])
        },
        components:{

        },
        mounted(){
            console.log(this.$store.state.isLoading)
        }
    }
</script>
