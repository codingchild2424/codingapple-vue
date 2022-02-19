<template>
    <div v-for = "(oneroom, i) in onerooms" :key="(oneroom, i)">
      <!-- <h1 @click = "popup = true; click = i">{{oneroom.title}}</h1> -->
      <img :src="oneroom.image" class = "img">
      <h4>{{oneroom.content}}</h4>
      <h4>{{oneroom.price}}원</h4>
    </div>
</template>

<script>
export default {
    name: 'CardComponent',
    props: {
        onerooms: Object,
        popup: Boolean,
    }

}
</script>

<style>

</style>