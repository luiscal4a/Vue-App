<template>
  <div class="hello">
  
    <div align="center">
      <table class="table">
        <thead>
          <tr>
            <th>First Name______</th>
            <th>Last Name______</th>
            <th>Age______</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td> {{ Product.name }}</td>
            <td>{{ Product.price }}</td>
            <td>{{ Product.category }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'hello',
  data() {
    return {
      Product: {},
    }
  },
  mounted() {
    axios.get('http://localhost:3002/api/product/')
      .then((response) =>{
      console.log(response.data);
      this.Product = response.data;
    })
    .catch((error) => {
      console.log(error);
    });
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
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