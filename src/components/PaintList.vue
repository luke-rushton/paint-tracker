<script setup>
import BlueSquare from './BlueSquare.vue/'
import GreySquare from './GreySquare.vue/'
import BlackSquare from './BlackSquare.vue/'
import WhiteSquare from './WhiteSquare.vue/'
import PurpleSquare from './PurpleSquare.vue/'
</script>

<template>
  <div class="main-list">
    <BlueSquare/>
    <GreySquare/>
    <BlackSquare/>
    <WhiteSquare/>
    <PurpleSquare/>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.main-list{
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
