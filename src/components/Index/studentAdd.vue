<template>
    <div class="content-right">
        <div class="console-child-title">
            <span>学生管理</span>
        </div>
        <div class="content-right-inner">
            <div class="form-horizontal">
                <div class="form-group">
                    <label for="" class="col-lg-1 control-label console-color-4">学生头像:</label>
                    <div class="col-lg-2">
                        <div class="upload-head upload-file">
                            <img :src="headImg" alt="" class="img-circle" style="width: 100px;height: 100px;background: #ccc">
                            <input type="file" @change="upload">
                        </div>
                        <input type="hidden" v-model="form.head" >
                    </div>
                    <p class="col-lg-5 console-line-3">
                        <!--这是错误信息-->
                    </p>
                </div>
                <div class="form-group">
                    <label for="" class="col-lg-1 control-label console-color-4"><span class="console-color-3">* </span>学生姓名:</label>
                    <div class="col-lg-4" :class="{'has-error':!status.name}">
                        <input type="text"  class="form-control" placeholder="" v-model="form.name" @input="check('name')" maxlength="12" minlength="2">
                    </div>
                    <p class="col-lg-5 console-line-2">
                        2-12位的汉字或英文
                    </p>
                </div>
                <div class="form-group">
                    <label for="" class="col-lg-1 control-label console-color-4">学生昵称:</label>
                    <div class="col-lg-4" :class="{'has-error':!status.nickName}">
                        <input type="text" class="form-control" placeholder="" v-model="form.nickName" @input="check('nickName')" maxlength="12" minlength="2">
                    </div>
                    <p class="col-lg-5 console-line-2">
                        2-12位的汉字或英文，不填写默认为姓名
                    </p>
                </div>
                <div class="form-group">
                    <label for="" class="col-lg-1 control-label console-color-4"><span class="console-color-3">* </span>登录帐号:</label>
                    <div class="col-lg-4" :class="{'has-error':!status.accounts}">
                        <input type="text" class="form-control" placeholder=""  v-model="form.accounts" @input="check('accounts')"
 maxlength="20" minlength="6">
                    </div>
                    <p class="col-lg-5 console-line-2">
                        6-20位的字母或数字的组合，推荐使用手机号或邮箱
                    </p>
                </div>
                <div class="form-group">
                    <label for="" class="col-lg-1 control-label console-color-4"><span class="console-color-3">* </span>登录密码:</label>
                    <div class="col-lg-4" :class="{'has-error':!status.password}">
                        <input type="text" class="form-control" placeholder="" v-model="form.password" @input="check('password')" maxlength="20" minlength="6">
                    </div>
                    <p class="col-lg-5 console-line-2">
                        6-20位的字母或数字的组合，默认：123456
                    </p>
                </div>
                <div class="form-group">
                    <label for="" class="col-lg-1 control-label console-color-4"><span class="console-color-3">* </span>选择性别:</label>
                    <div class="col-lg-4">
                        <label class="radio-inline">
                            <input type="radio" name="sex" v-model="form.sex" value="0"> 男
                        </label>
                        <label class="radio-inline">
                            <input type="radio" name="sex" v-model="form.sex" value="1"> 女
                        </label>
                    </div>
                </div>
                <div class="form-group">
                    <label for="" class="col-lg-1 control-label console-color-4"><span class="console-color-3">* </span>学生类型:</label>
                    <div class="col-lg-4">
                        <label class="radio-inline">
                            <input type="radio" name="status" v-model="form.status" value="1"> 正式
                        </label>
                        <label class="radio-inline">
                            <input type="radio" name="status" v-model="form.status" value="0"> 非正式
                        </label>
                    </div>
                </div>
                <div class="form-group">
                    <label for="" class="col-lg-1 control-label console-color-4">教师介绍:</label>
                    <div class="col-lg-4">
                        <textarea name="" v-model="form.desc" class="form-control" cols="30" rows="10" maxlength="5000"></textarea>
                    </div>
                    <p class="col-lg-5 console-line-2">
                        {{form.desc.length}}/5000个字符
                    </p>
                </div>
                <div class="form-group">
                    <label for="" class="col-lg-1 control-label console-color-4"></label>
                    <div class="col-lg-4">
                        <input type="submit" value="提交" class="btn btn-info" @click="submit()">
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
    export default{
        data(){
            return {
                //表单值记录
                headImg:'',
                form:{
                    head:'',
                    name:'',
                    nickName:'',
                    sex:0,
                    status:1,
                    desc:0,
                    accounts:'',
                    password:'123456'
                },
                submitStatus:false,
                //状态记录
                status:{
                    name:false,
                    nickName:false,
                    accounts:false,
                    password:true,
                },
                pattern:{
                    name:/^([\u4E00-\uFA29]|[\uE7C7-\uE7F3]|[a-zA-Z0-9_]){2,12}$/,
                    nickName:/^([\u4E00-\uFA29]|[\uE7C7-\uE7F3]|[a-zA-Z0-9_]){2,12}$/,
                    accounts:/^\w{6,20}$/,
                    password:/^\w{6,20}$/,
                }
            }
        },
        methods:{
            check(data){
                if(this.pattern[data].test(this.form[data])){

                    this.status[data]=true;
                    return true;
                }
                else{
                    this.status[data]=false;
                    return false
                }
            },
            upload(e){
                console.log(e);
                let file = e.target.files[0];
                let form = new FormData();
                form.append('file',file,file.name);
                let config = {
                    headers:{'Content-Type':'multipart/form-data'}
                };  //添加请求头
                this.$http.post('http://127.0.0.1:8081/uploading',form,config)
                    .then(response=>{
                        console.log(response.data);
                        let img=response.data.file[0].path.replace(/\\/g,"/");
                        this.form.head=img;
                        this.headImg=IMG_ROOT+img
                    })
            },
            submit(){
                for(let i in this.status){
                    if(this.status[i]==false){
                        this.submitStatus=false;
                        break;
                    }else{
                        this.submitStatus=true;
                        continue;
                    }
                }
                if(this.submitStatus)
                {
                    alert(1)
                }
            }
        }
    }
</script>