<template>
  <div class="photogrid">
    <div class="loading" v-if="isLoading">
      <div class="photo__row__loader">
        <div class="photo__column__loader">
          <div class="author__info__loader">
            <p></p>
            <p class="author__info__location__loader"></p>
          </div>
        </div>


        <div class="photo__column__loader">
          <div class="author__info__loader">
            <p></p>
            <p class="author__info__location__loader"></p>
          </div>
        </div>

        <div class="photo__column__loader">
          <div class="author__info__loader">
            <p></p>
            <p class="author__info__location__loader"></p>
          </div>
        </div>

        

        
      </div>
    </div>

 
    <div class="photo__row">
      <div class="photo__column" v-for="item in images" :key="item.id">
       
        <img :src="item.urls.regular" />


        <div class="author__info">
          <p>{{item.user.name}}</p>
          <p class="author__location">{{item.user.location}}</p>


       
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
  position: relative;

   
}
.photo__column > img {
  border-radius: 10px;
  width: 100%;

  z-index: 1;

  filter: brightness(0.7);
 
}

.overlay{
   
}

.author__info {
  position: absolute;
  left: 15px;
  right: 0;
  top: 40%;
  bottom: 27px;
 
  color: #fff;
  display: flex;
  flex-direction: column;
  justify-content:flex-end;
  text-transform: capitalize;
} 

.author__info >.author__location{
  font-size:small;
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
  
  height: 400px;
  background: #f0f0f0;
  width: 100%;
  border-radius: 20px;
  position: relative;

  
  width: 100%;
    padding-top: 10%;
    border-radius: 20px;
}

.author__info__loader{
   position: absolute;
  left: 15px;
  right: 0;
  top: 40%;
  bottom: 27px;
  display: flex;
  flex-direction: column;
  justify-content:flex-end;
  text-transform: capitalize;
 
  color: red;


  
}
.author__info__loader > p{
  background-color: #ddd;
    width:131px;
  height:15px;
  margin-bottom:16px;
    animation: pulse-bg 1s infinite;

}

.author__info__loader > .author__info__location__loader{
     width:80px;


}

@keyframes pulse-bg {
    0% { background-color: #ddd; }
    50% { background-color: #d0d0d0; }
    100% { background-color: #ddd; }
  }
/* media queries */

@media (max-width: 1200px) {
  .photo__row {
    columns: 2;
  }


  .photo__row__loader{
    columns: 1;

  }
}

@media (max-width: 768px) {
  .photo__row {
    columns: 1;
  }

  .photo__row__loader{
    columns: ;

  }
}

@media (max-width: 480px) {
  .photo__row {
    columns: 1;
  }

.photo__row__loader{
    columns: 1;

  }

}


</style>
