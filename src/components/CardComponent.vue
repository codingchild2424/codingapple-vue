<template>
    <div v-for = "oneroom in onerooms" :key="oneroom">
      <h1 @click = "$emit('openModal', oneroom.id)">{{oneroom.title}}</h1>
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