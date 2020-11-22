
<template>
  <div>
   

   PhotoGrid.cov

   <div v-for="item in africaImages" :key="item.id">

       <img :src="item.urls.full" width="50"/>
       
     </div>
  </div>
</template>

<script>
export default {
  name: 'PhotoGrid',
  created() {

  },
  data() {
    return {
    }
  },
  props: {
africaImages:Array

   
  },
  methods: {
   
  },
}
</script>

<style lang="scss" scoped>

</style>

