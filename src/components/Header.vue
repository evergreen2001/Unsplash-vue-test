<template>
  <section class="header">
    <div class="search__container">
      <i class="fa fa-search search__icon"></i>
      <input type="search" placeholder="Search for photo" />
    </div>
  </section>
</template>

<script>
export default {
  name: "Header",
  created() {},
  data() {
    return {};
  },
  props: {},
  methods: {},
};
</script>

<style>
.header {
  background: var(--backdrop-color);
  height: var(--backdrop-height);
  padding-top: 80px ;
 
}

.search__container {
  margin-top: 90px;

  display: flex;

  align-items: center;
  margin: auto;
  /* padding: 10px 0; */

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
  padding-left: 70px;
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
  padding: 20px;
}
</style>
