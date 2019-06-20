<template>
  <div class="details container">
    <button type="button" @click="$router.back(-1)">返回</button>
    <h1 class="page-header">
        {{coustmer.name}}

        <span class="pull-right">
            <router-link class="btn btn-primary" :to="'/edit/'+coustmer.id">编辑</router-link>
            <button class="btn btn-danger" @click="deleteCoustmer(coustmer.id)">删除</button>
        </span>

    </h1>
    <ul class="list-group">
        <li class="list-group-item"><span class="glyphicon glyphicon-phone"> {{ coustmer.phone }}</span></li>
        <li class="list-group-item"><span class="glyphicon glyphicon-envelope"> {{ coustmer.email }}</span></li>
    </ul>

    <ul class="list-group">
        <li class="list-group-item"><span class="glyphicon glyphicon-heart"> {{ coustmer.age }}</span></li>
        <li class="list-group-item"><span class="glyphicon glyphicon-equalizer"> {{ coustmer.companyId }}</span></li>
    </ul>
    
  </div>
</template>

<script>
export default {
  name: 'detail',
  data () {
    return {
      coustmer:""
    }
  },
  methods: {
    fetchCoustmers(id){
        
      this.$axios.get('http://localhost:3000/user/'+id)
      .then((res)=>{
        this.coustmer = res.data;
      })
    },
    deleteCoustmer(id){
        console.log(id)
        this.$axios.delete('http://localhost:3000/user/'+id)
        .then((res)=>{
            this.$router.push({path:"/",query:{alert:"删除成功！"} })
        }) 
    }
  },
  created() {
      
      this.fetchCoustmers(this.$route.params.id)
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
