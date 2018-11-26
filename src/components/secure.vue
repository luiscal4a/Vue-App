<template>
    <div id="secure">
        <h1>Secure Area</h1>
        <p>
            {{ myData }}
        </p>
    </div>
</template>

<script>
    export default {
  name: 'secure',
  data() {
    return {
      myData: "Loading Products...",
      token: this.$route.params.token
    }
  },
  methods:{
    async start(){
    const httpOptions = {
        'Authorization': 'Beacon ' + this.token,
        'Access-Control-Allow-Origin': '*'
      }

      const response = await this.axios.get('http://localhost:3002/api/product/', {headers: httpOptions});
      //console.log(response.data.products[0]);
      this.myData = response.data.products;
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

<style scoped>
    #secure {
        background-color: #FFFFFF;
        border: 1px solid #CCCCCC;
        padding: 20px;
        margin-top: 10px;
    }
</style>