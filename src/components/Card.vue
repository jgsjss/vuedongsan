<template>
  <div >
    <img class="room-img" :src="product.image">
    <h4 @click="$emit('openModal', product.id)">{{product.title}}</h4>
    <p>{{product.content}}</p>
    <p>월세 : {{product.price}} 원</p>
  </div>
</template>

<script>
export default {
  props :{
      product : Object,
  }
   
}
</script>

<style>

</style>