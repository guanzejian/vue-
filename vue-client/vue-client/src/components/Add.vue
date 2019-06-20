<template>
  <div class="add container">
    <Alert v-if="alert" :message="alert"></Alert>
    <h1 class="page-header">添加用户</h1>
    <form @submit="addCoustmer">
        <div class="well">
            <h4>用户信息</h4>
            <div class="form-group">
                <label>姓名</label>
                <input type="text" class="form-control" placeholder="name" v-model="coustmer.name">
            </div>
            <div class="form-group">
                <label>电话</label>
                <input type="text" class="form-control" placeholder="phone" v-model="coustmer.phone">
            </div>
            <div class="form-group">
                <label>邮箱</label>
                <input type="text" class="form-control" placeholder="email" v-model="coustmer.email">
            </div>
            <div class="form-group">
                <label>年纪</label>
                <input type="text" class="form-control" placeholder="age" v-model="coustmer.age">
            </div>
            
            <div class="form-group">
                <label>公司ID</label>
                <textarea class="form-control" rows="10" v-model="coustmer.companyId"></textarea>
            </div>
            <button type="submit" class="btn btn-primary">添加</button>
        </div>
    </form>
  </div>
</template>

<script>
import Alert from "./alert"

export default {
  name: 'add',
  data () {
    return {
      coustmer:{},
      alert:""
    }
  },
  methods: {
      addCoustmer(e){
          if(!this.coustmer.name || !this.coustmer.phone || !this.coustmer.email){
             this.alert = "请填写对应的信息！"
          }else{
              let newCoustmer = {
                  name:this.coustmer.name,
                  phone: this.coustmer.phone,
                  email: this.coustmer.email,
                  age: this.coustmer.age,
                  companyId: this.coustmer.companyId
              }
              this.$axios.post("http://localhost:3000/user",newCoustmer)
              .then(res=>{
                  this.$router.push({path:"/",query:{alert:"用户信息添加成功！"} });
              })
          }
          e.preventDefault();

      }
  },
  components:{
      Alert
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
