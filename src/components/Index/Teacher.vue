<template>
    <router-view></router-view>
</template>
<script>
    import Page from '../public/Page.vue'
    export default{
        data(){
            return {
                list:[
                    {
                        name:'张志军',
                        id:'123',
                        nickName:'昵称',
                        sex:'男',
                        status:'否',
                        accounts:'3710000',
                        password:'123',
                        create_time:'2017.06.05 19:23'
                    },
                    {
                        name:'张志军',
                        id:'123',
                        nickName:'昵称',
                        sex:'男',
                        status:'否',
                        accounts:'37102130',
                        password:'456',
                        create_time:'2017.06.05 19:23'
                    }
                ]
            }
        },
        components:{
            page:Page
        },
        methods:{
            delTeacher(index,id){
                if(confirm('确定要删除么')){
                    this.list.splice(index,1);
                }
            },
            alterTeacher(name,password){
                let alter=prompt('正在修改'+name+'的密码',password);
                if(alter){
                    if(/^\w{6,20}$/.test(alter)){
                        alert('修改成功')
                    }else{
                        alert('修改失败')
                    }
                }
            },
            pageIndex(data){
                console.log(data)
            }
        }
    }
</script>