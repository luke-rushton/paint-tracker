<template>
  <div class="product-block">
    <div class="square">
      <h3>White</h3>
    </div>
    <div>
      <p v-if="data">Quantity: {{ data.Amount }}</p>
      <p>Add to Stock</p>
      <input type="number" v-model="addAmount"/>
      <button @click="updateData(addAmount)">add</button>
      <p>Remove from stock</p>
      <input type="number" v-model="removeAmount"/>
      <button @click="updateData(-removeAmount)">remove</button>
    </div>
  </div>
</template>

<script>
export default {
    data() {
      return {
        data: null,
      };
    },
    methods: {
      async fetchData() {      
        const response = await fetch("https://tklsyjqrt9.execute-api.us-west-1.amazonaws.com/items/white"); 
        this.data = await response.json();
      },
      async updateData(updateAmount) {
        this.fetchData(); //ensure we have current stock quantity
        if ((this.data.Amount + updateAmount) < 0){ //check to see if operation will result in negative stock
          alert("Error: Can\'t have less than 0 paint in stock. ")
        } else { //update to new stock quantity
          const sendData = await fetch("https://tklsyjqrt9.execute-api.us-west-1.amazonaws.com/items", {
            method: "PUT",
            headers: {
              "Content-Type": "application/json",
            },
            body: "{\"PaintColor\":\"white\",\"Amount\":" + (this.data.Amount + updateAmount) + "}"
          });
        }
        this.fetchData(); //refresh stock quantity display
      }   
    },
    created() {
      this.fetchData(); //loads stock quantity
    }
  };
</script>

<style scoped>
.product-block{
  display: flex;
  border: 3px solid black;
  padding: 5px;
  border-radius: 15px;
  margin: 5px;
}
.square{
  height: 150px;
  width: 150px;
  background-color: white;
  margin: 5px;
  border-radius: 15px;
  display: flex;
  justify-content: center;
}
.square h3{
  color: white;
  font-weight: bold;
  text-shadow: 0 0 3px black;
}
</style>
