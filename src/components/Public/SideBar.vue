<template>
    <div class='content'>
        <ul class='content-left-nav'>
            <li v-for='item in json.menuList[id].list'>
                <h5>{{item.title}}</h5>
                <dl>
                    <dd v-for='items in item.list'>
                        <router-link :to="{name:items.router}">{{items.name}}</router-link>
                    </dd>
                </dl>
            </li>
        </ul>
        <div class='content-right-inner'>
            <router-view></router-view>
        </div>
    </div>
</template>
<script>
    import json from '../../menu.json';
    export default {
        components: {
        },
        data(){
            return {
                id:0,
                json:json
            }
        },
        methods:{
        },
        mounted(){
            var that=this;
            this.$watch('message', function(newVal, oldVal){
                that.id=newVal;
                console.log(that.id);
            });
        },
        props:['message']
    }
</script>