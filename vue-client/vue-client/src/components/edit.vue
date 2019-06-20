<template>
  <div class="edit container">
<Alert v-if="alert" :message="alert"></Alert>
    <h1 class="page-header">编辑用户信息</h1>
    <form @submit="editCoustmer">
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
            <button type="submit" class="btn btn-primary">确认</button>
        </div>
    </form>
  </div>
</template>

<script>
import Alert from "./alert"

export default {
  name: 'edit',
  data () {
    return {
      coustmer:{},
      alert:""
    }
  },
  methods: {
      fetchCoustmer(id){
          this.$axios.get("http://localhost:3000/user/"+id)
          .then(res=>{
              this.coustmer = res.data;
          })
      },
      editCoustmer(e){
          if(!this.coustmer.name || !this.coustmer.phone || !this.coustmer.email){
              this.alert = "请填写对应的信息"
          }else{
              let newCoustmer = {
                  name:this.coustmer.name,
                  phone: this.coustmer.phone,
                  email: this.coustmer.email,
                  age: this.coustmer.age,
                  companyId: this.coustmer.companyId
              }
              this.$axios.put("http://localhost:3000/user/"+this.$route.params.id,newCoustmer)
              .then(res=>{
                  this.$router.push({path:"/",query:{alert:"用户信息更新成功！"} });
              })
          }
          e.preventDefault();

      }
  },
  created() {
      this.fetchCoustmer(this.$route.params.id);
  },
  components:{
      Alert
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
