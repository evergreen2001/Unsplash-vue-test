<template>
  <div class="photogrid">
    <div class="loading" >
      <div class="photo__row__loader">
        <div class="photo__column__loader">
          <div class="author__info">
            <p>username</p>
            <p>location</p>
          </div>
        </div>

        <div class="photo__column__loader">
          <div class="author__info">
            <p>username</p>
            <p>location</p>
          </div>
        </div>

        <div class="photo__column__loader">
          <div class="author__info">
            <p>username</p>
            <p>location</p>
          </div>
        </div>

        <div class="photo__column__loader">
          <div class="author__info">
            <p>username</p>
            <p>location</p>
          </div>
        </div>

        <div class="photo__column__loader">
          <div class="author__info">
            <p>username</p>
            <p>location</p>
          </div>
        </div>

        <div class="photo__column__loader">
          <div class="author__info">
            <p>username</p>
            <p>location</p>
          </div>
        </div>
      </div>
    </div>

    <!-- <div> <h2> Loading </h2></div> -->
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
    isLoading: Boolean,
  },
  methods: {},
};
</script>

<style scoped>
.photogrid {
  width: 77%;
  margin: auto;
}
.photo__row {
  max-width: 1200px;
  margin: 30px auto;
  padding: 0px 20px;

  columns: 3;
  column-gap: 60px;
}

.photo__column {
  margin: 0 0 20px 0;
  width: 100%;
}
.photo__column > img {
  border-radius: 10px;
  width: 100%;

  z-index: 1;
  transition-duration: 0.3s;
  transition-property: all;
  transition-timing-function: ease-out;
  transform: translateZ(0);
}

.author__info {
  color: #fff;
  font-weight: 800;

  position: absolute;

  bottom: 10%;
  left: 16px;
}

/* media queries */

@media (max-width: 1200px) {
  .photo__row {
    columns: 2;
  }
}

@media (max-width: 768px) {
  .photo__row {
    columns: 2;
  }
}

@media (max-width: 480px) {
  .photo__row {
    columns: 2;
  }
}

/* Skeleton loader  */
.photo__row__loader {
  margin: 30px auto;
  padding: 0px 20px;

  columns: 3;
  column-gap: 60px;
}

.photo__column__loader {
  margin: 0 0 20px 0;
  /* height: 800px; */
  /* background-color:linear-gradient(-45deg, #DDDDDD,, #DDDDDD, #F0F0F0);
  */
  height: 400px;
  background: #f0f0f0;
  width: 100%;
  border-radius: 20px;
  animation: shine 1s infinite;
}

@keyframes shine {
  to {
    background-position: 0 0, 100% 0, /* move highlight to right */ 120px 0,
      120px 40px, 120px 80px, 120px 120px;
  }
}
</style>
