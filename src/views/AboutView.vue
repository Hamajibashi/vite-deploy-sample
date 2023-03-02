<template>
  <div class="about">
    <h1>This is an about page</h1>
    <hr>
    <button @click="getData">取個名字吧</button>
      {{user}}
  </div>
</template>
<script>
export default {
  data(){
    return{
      user:'',
    }
  },
  methods:{
    getData(){
      this.$http.get('https://randomuser.me/api/')
      .then(res=>{
        this.user = res.data.results[0].name.first;
      })
    }
  },
  mounted(){
    console.log(import.meta.env.VITE_TEXT);
  }
}
</script>
<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
button{
  width: 150px;
  padding: 8px 16px;
  border-radius: 8px;
}
</style>
