<template>
    <div v-if = "popup == true" class="black-bg">
        <div class="white-bg">
            <h4>{{onerooms[click].title}}</h4>
            <img :src="onerooms[click].image" class = "img">
            <!-- <button @click="popup = false">닫기</button> -->
        </div>
    </div>
</template>

<script>
export default {
    name: 'ModalComponent',
    props : {
        popup: Boolean,
        onerooms: Array,
        click: Number,
    }
}
</script>

<style>
.black-bg {
  width: 80%; height: 60%;
  background: rgba(0,0,0,0,5);
  position: fixed; padding: 20px;
}

.white-bg {
  width: 80%; background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>