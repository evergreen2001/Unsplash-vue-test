<template>
  <section class="header">
    <div class="search__result__text" v-if="searching">
      <h1>
        Search result for <span>"{{ searchQuery }}"</span>
      </h1>
    </div>
    <div class="search__container" v-else>
      <i class="fa fa-search search__icon"></i>
      <input
        type="search"
        placeholder="Search for photo"
        v-model="searchQuery"
        @keyup.enter="handleSearch"
      />
    </div>

    <PhotoGrid :images="images" :isLoading='isLoading' />
  </section>
</template>

<script>
import PhotoGrid from "./PhotoGrid";
import axios from "axios";
export default {
  name: "Header",
  created() {
    //making a GET request to get 8 latest "African photos"
    this.isLoading = true;
    axios
      .get("https://api.unsplash.com/search/photos", {
        params: {
          query: this.query,
          client_id: "6BguTKo0SLW85C-gWpQsP5WGxMvtSQfDJBXZRLi0LTE",
          
          page: 1,
        },
      })
      .then((res) => {
        console.log(res.data.results);
        this.images = res.data.results;
      }).finally(()=>{
          this.isLoading = false;
        });
  },
  data() {
    return {
      inputValue: "",
      images: [],
      page: 1,
      query: "Africa",
      searchQuery: [],
      searching: false,
      isLoading: false


    };
  },
  props: {},
  methods: {
    handleSearch() {
      this.searching = true;
      this.newest = false;
      this.isLoading  = true;
      console.log("Search started");
      axios
        .get("https://api.unsplash.com/search/photos", {
          params: {
            query: this.searchQuery,
            client_id: "6BguTKo0SLW85C-gWpQsP5WGxMvtSQfDJBXZRLi0LTE",
           
            page: 1,
          },
        })
        .then((response) => {
          this.images = response.data.results;
          console.log(response);
        })
        .catch((e) => {
          this.erorrs.push(e);
        }).finally(()=>{
          this.isLoading = false;
        });
    },
  },
  components: {
    PhotoGrid,
  },
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

.search__result__text {
  padding: 5px 0;
  margin-top: 90px;

  display: flex;

  align-items: center;
  margin: auto;
  padding: 5px 0;

  border-radius: 10px;

  width: 80%;
}

.search__result__text > h1 {
  font-size: 40px;
  color: var(--dark-blue);
  font-weight: 900;
}

.search__result__text > h1 > span {
  font-size: 40px;
  color: var(--light-blue);
  font-weight: 900;
}


</style>
