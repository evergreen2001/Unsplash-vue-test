<template>
  <div class="photogrid">
    <div class="photo__row">
      <div class="photo__column" v-for="item in images" :key="item.id">
        <img :src="item.urls.regular" />

        <div class="author__info">
          <p>username</p>
          <p>location</p>
        </div>
      </div>
    </div>

    <div></div>
  </div>
</template>

<script>
export default {
  name: "PhotoGrid",
  created() {},
  data() {
    return {};
  },
  props: {
    images: Array,
  },
  methods: {

    
  },
};
</script>

<style scoped>
.photogrid {
  width: 100%;
  margin: auto;
}
.photo__row {
  /* max-width: 1200px; */
  margin: 30px auto;
  padding: 0 20px;
 position: relative;
  display: grid;
  /* Define Auto Row size */

  /*Define our columns */
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  grid-gap: 0.7em;
}

.photo__column {
  /* height: 100%; */
  margin: 30px;
  position: relative;
}
.photo__column > img {
  border-radius: 10px;

  top: 0;
  left: 0;
  width: 100%;
  height: auto;
  z-index: 1;
  transition-duration: 0.3s;
  transition-property: all;
  transition-timing-function: ease-out;
  transform: translateZ(0);
}

.author__info  {
  color: #fff;
  font-weight: 800;

  position: absolute;
  /* top: 30px; */

  
  bottom: 10%;
  left: 16px;
}
</style>
