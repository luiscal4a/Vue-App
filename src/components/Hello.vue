<template>
  <div class="hello">
  
    <div align="center">
      <b-table class="table">
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
      </b-table>
    </div>
  
  </div>
</template>

<script>

const items = [
  { isActive: true, age: 40, first_name: 'Dickerson', last_name: 'Macdonald' },
  { isActive: false, age: 21, first_name: 'Larsen', last_name: 'Shaw' },
  { isActive: false, age: 89, first_name: 'Geneva', last_name: 'Wilson' },
  { isActive: true, age: 38, first_name: 'Jami', last_name: 'Carney' }
]
  
export default {
  name: 'hello',
  data() {
    return {
      items: items
    }
  },
  methods:{
    async start(){
      const response = await this.axios.get('http://localhost:3002/api/product/');
      console.log(response.data.products[0]);
      this.Product = response.data.products[0];
    }
  },
  mounted() {
    this.start();
    /*axios.get('http://localhost:3002/api/product/')
      .then((response) =>{
      console.log(response.data);
      console.log(response.data);
      this.Product = response.data;
    })
    .catch((error) => {
      console.log(error);
    });*/
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