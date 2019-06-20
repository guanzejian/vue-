<template>
  <div class="coustmer container">
    <Alert v-if="alert" :message="alert"></Alert>
    <h1 class="page-header">用户管理系统</h1>
    <input type="text" class="form-control" placeholder="搜索" v-model="filterInput">
    <table class="table table-striped">
      <thead>
        <tr>
          <th>ID</th>
          <th>姓名</th>
          <th>电话</th>
          <th>邮箱</th>
          <th>操作</th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="coustmer in filterBar(coustmers,filterInput)" :key="coustmer.id">
          <td>{{ coustmer.id }}</td>
          <td>{{ coustmer.name }}</td>
          <td>{{ coustmer.phone }}</td>
          <td>{{ coustmer.email }}</td>
          <td><router-link class="btn btn-default" :to='"/coustmer/"+coustmer.id'>详情</router-link></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import Alert from "./alert"

export default {
  name: 'coustmer',
  data () {
    return {
      coustmers:[],
      alert:"",
      filterInput:""
    }
  },
  created() {
    if(this.$route.query.alert){
      this.alert = this.$route.query.alert
    }
    this.fetchCoustmers();
  },
  updated() {
    this.fetchCoustmers();
  },
  methods: {
    fetchCoustmers(){
      var that = this;
      this.$axios.get('http://localhost:3000/user')
      .then(function(res){
        that.coustmers = res.data;
      })
    },
    filterBar(coustmers,value){
      return coustmers.filter(function(coustmer){
        return coustmer.name.match(value)
      })
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
