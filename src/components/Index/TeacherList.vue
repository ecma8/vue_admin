<template>
    <div class="content-right">
        <div class="console-child-title">
            <span>教师管理</span>
        </div>
        <div class="content-right-inner">
            <div class="form-inline console-form-title">
                <div class="form-group pull-left col-lg-1">
                    <select id="" class="form-control">
                        <option value="1">姓名</option>
                        <option value="2">类型</option>
                        <option value="3">昵称</option>
                        <option value="4">帐号</option>
                        <option value="5">创建日期</option>
                    </select>
                </div>
                <div class="form-group col-lg-2">
                    <input type="text" class="form-control" placeholder="">
                </div>
                <div class="form-group col-lg-1">
                    <input type="button" value="查询" class="btn btn-default" id="123">
                </div>
                <div class="form-group pull-right col-lg-1">
                    <router-link :to="{name:'teacherAdd'}" class="btn btn-info">添加老师</router-link>
                </div>
                <a href="" class="pull-right col-lg-1 console-color">批量导入</a>
                <a href="" class="pull-right col-lg-1 console-color">批量导出</a>
            </div>
            <table class="console-table">
                <thead>
                <tr>
                    <th>姓名</th>
                    <th>昵称</th>
                    <th>性别</th>
                    <th>授课</th>
                    <th>帐号</th>
                    <th>注册/创建日期</th>
                    <th class="col-lg-2">操作</th>
                </tr>
                </thead>
                <tbody>
                <tr>
                    <td>1</td>
                    <td>1</td>
                    <td>1</td>
                    <td>1</td>
                    <td>1</td>
                    <td>1</td>
                    <td>
                        <a href="" class="console-color-1">编辑</a>
                        <a href="" class="console-color-1">修改密码</a>
                        <a href="" class="console-color-2">删除</a>
                    </td>
                </tr>
                <tr>
                    <td></td>
                    <td></td>
                    <td></td>
                    <td></td>
                    <td></td>
                    <td></td>
                    <td>
                        <a href="" class="console-color-1">编辑</a>
                        <a href="" class="console-color-1">修改密码</a>
                        <a href="" class="console-color-2">删除</a>
                    </td>
                </tr>
                <tr>
                    <td></td>
                    <td></td>
                    <td></td>
                    <td></td>
                    <td></td>
                    <td></td>
                    <td>
                        <a href="" class="console-color-1">编辑</a>
                        <a href="" class="console-color-1">修改密码</a>
                        <a href="" class="console-color-2">删除</a>
                    </td>
                </tr>
                </tbody>
                <tfoot>
                <tr>
                    <td colspan="8">
                        <page :pages=10 :curr=1 v-on:pageIndex="pageIndex"></page>
                        <span>共6页 每页显示五条</span>
                    </td>
                </tr>
                </tfoot>
            </table>
        </div>

        <router-view></router-view>
    </div>
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
                ],
            }
        },
        mounted(){
        },
        components:{
            page:Page,
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