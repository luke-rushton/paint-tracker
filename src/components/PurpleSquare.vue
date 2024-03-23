<script setup>
defineProps({
  colour: {
    type: String,
    required: true
  }
})
const tester = "--red"
</script>

<template>
  <div class="product-block">
    <div class="square">
      <h3>Purple</h3>
    </div>
    <div>
      <p>Quantity: 0</p>
      <p>Add to Stock</p>
      <input type="number"/>
      <button>add</button>
      <p>Remove from stock</p>
      <input type="number"/>
      <button>remove</button>
    </div>
  </div>
</template>

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
  background-color: purple;
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