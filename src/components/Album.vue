<template>
  <div>
  <img class="preview-img" v-for="(item, index) in list" :src="item.src" width="400" height="400" @click="$preview.open(index, list)">
  </div>
</template>

<script>
export default {
  name: 'Album',
  data () {
    return {
      list: [{
        src: '/static/upload/img/1.jpg',
        w: 400,
        h: 400
      }, {
        src: '/static/upload/img/2.jpg',
        w: 400,
        h: 400
      }, {
        src: '/static/upload/img/3.jpg',
        w: 400,
        h: 400
      }, {
        src: '/static/upload/img/4.jpg',
        w: 400,
        h: 400
      }, {
        src: '/static/upload/img/5.jpg',
        w: 400,
        h: 400
      }, {
        src: '/static/upload/img/6.jpg',
        w: 400,
        h: 400
      }, {
        src: '/static/upload/img/7.jpg',
        w: 400,
        h: 400
      }, {
        src: '/static/upload/img/8.jpg',
        w: 400,
        h: 400
      }, {
        src: '/static/upload/img/9.jpg',
        w: 400,
        h: 400
      }, {
        src: '/static/upload/img/10.jpg',
        w: 400,
        h: 400
      }, {
        src: '/static/upload/img/11.jpg',
        w: 400,
        h: 400
      }, {
        src: '/static/upload/img/12.jpg',
        w: 400,
        h: 400
      }]
    }
  }
}
</script>
<style scoped>
.preview-img{
  margin-left: 20px;
}
</style>
