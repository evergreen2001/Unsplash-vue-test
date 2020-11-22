<template>
  <section class="header">
    <div class="search__container">
      <i class="fa fa-search search__icon"></i>
      <input
        type="search"
        placeholder="Search for photo"
        v-model="inputValue"
      />
    </div>

     
     <PhotoGrid :africaImages="africaImages"/>
  </section>
</template>

<script>
import PhotoGrid from './PhotoGrid'
import axios from "axios";
export default {
  name: "Header",
  created() {
    //making a GET request to get 8 latest "African photos"
    axios
      .get("https://api.unsplash.com/search/photos", {
        params: {
          query: this.query,
          client_id: "6BguTKo0SLW85C-gWpQsP5WGxMvtSQfDJBXZRLi0LTE",
          order_by: "latest",
          per_page:"8"

        },
      })
      .then((res) => {
        console.log(res.data.results);
        this.africaImages = res.data.results
      });
  },
  data() {
    return {
      inputValue: "",
      africaImages: [],
      page: 1,
      query:'Africa'
    };
  },
  props: {},
  methods: {},
  components:{
    PhotoGrid
  }
};
</script>

<style>
.header {
  background: var(--backdrop-color);
  height: var(--backdrop-height);
  padding-top: 80px;
}

.search__container {
  margin-top: 90px;

  display: flex;

  align-items: center;
  margin: auto;
  padding: 5px 0;

  border-radius: 10px;
  background-color: #fff;
  width: 80%;
}

.search__container > input {
  border: none;
  outline-width: none;
  background: #fff;
  font-family: Poppins;
  height: 20px;
  padding-left: 10px;
  border-radius: 10px;
  border: none;
  font-size: 20px;
  width: 70%;
  max-width: 100%;
  color: var(--navy-blue);
  outline: none;
}
.search__icon {
  font-size: 20px;
  color: var(--navy-blue);
  background-color: #fff;
  border-radius: 10px;
  padding: 20px 40px;
  font-weight: 100;
}
</style>
