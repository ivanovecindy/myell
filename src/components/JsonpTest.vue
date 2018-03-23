<template>
  <div  >
    <h1>{{ msg }}</h1>
    <table>
      <tr v-for="item in newData">
        <td>{{item.id}}</td>
        <td>{{item.title}}</td>
        <td><img :src="item.url"/></td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: 'JsonpTest',
  data () {
    return {
      msg: 'Welcome to JsonpTest',
      newData:[]
    }
  },
  created(){
     this.$axios('http://jsonplaceholder.typicode.com/photos',{
       params:{
       }
     }).then((res) => {
        console.log(res.data);
       this.newData=res.data;
     }).catch(error=>{
       console.log(error);
     })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
