<template>
  <div>
    <table>
      <tr>
        <th>ID</th>
        <th>Image</th>
        <th>title</th>
        <th>Menu Link</th>
      </tr>
      <tr v-for="(item,i) in data" :key="i">
        <td>{{item.id}}</td>
        <td> <img :src="item.image" alt="Girl in a jacket" width="100" height="100"></td>
        <td>{{item.title}}</td>
        <td> <a href="javascript:;" @click="id = item.id">{{item.menu_link}}</a></td>
      </tr>
      
    </table>
      <div v-if="data.length > 0">
        <h1>{{data[id - 1].title}}</h1>
        <p>{{data[id - 1 ].body}}.</p>
      </div>
      

  </div>
</template>

<script>
export default {
  name: 'Mocky',
  props: {
  },
  data(){
    return {
      api : "http://www.mocky.io/v2/5e6644ed3100001dcd239e3d",
      data : [
        
      ],
      id: 1
    }
  },
  created(){
    this.getData()
  },
  methods:{
    async getData(){
      await fetch(this.api)
          .then(response => response.json())
          .then(data => this.data = data);
    },

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

td, th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #dddddd;
}
</style>
