<template>
  <div class="home-page">
    <section class="intro">
      <h1>Get the latest tech mews!</h1>
    </section>
    <ListProducts :products="loadedProducts" />
  </div>
</template>

<script>
import ListProducts from '@/components/Products/ListProducts'
export default {
  components: {
    ListProducts
  },
/*   data(){
    return{
      loadedProducts:[
        {
          id:'1',
          name: 'Galleta',
          price: '3.58',
          description: 'Galleta rellena de chocolate',
          thumbnailLink: 'https://cdn7.kiwilimon.com/recetaimagen/3329/640x426/th5-640x426-38990.jpg.webp',
          category:{
            id:'1',
            name:'Chatarra'
          }
        },
        {
          id:'2',
          name: 'Galletita',
          price: '3.58',
          description: 'Galletatita rellena de chocolate',
          thumbnailLink: 'https://cdn7.kiwilimon.com/recetaimagen/3329/640x426/th5-640x426-38990.jpg.webp',
          category:{
            id:'1',
            name:'Chatarra'
          }
        }
      ]
    }
  } */
  computed:{
    loadedProducts(){
      return this.$store.getters.loadedProducts
    }
  }
}
</script>

<style scoped>
.intro {
  height: 300px;
  position: relative;
  padding: 30px;
  box-sizing: border-box;
  
  background-position: center;
  background-size: cover;
}

.intro h1 {
  position: absolute;
  top: 10%;
  left: 5%;
  width: 90%;
  font-size: 1.5rem;
  color: black;
  background-color: rgb(211, 211, 211);
  padding: 10px;
  border-radius: 10px;
  box-shadow: 3px 3px 3px black;
  box-sizing: border-box;
  border: 1px solid black;
}

@media (min-width: 768px) {
  .intro h1 {
    font-size: 2rem;
  }
}

.featured-posts {
  display: flex;
  padding: 20px;
  box-sizing: border-box;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
}


</style>