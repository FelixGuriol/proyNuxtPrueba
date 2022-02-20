<template>
    <div class="posts-page">
        <ListProducts :products="loadedProducts" />
    </div>
</template>

<script>
import ListProducts from '@/components/Products/ListProducts'
export default {
    components: {
    ListProducts
  },
  data(){
    return{
      loadedProducts:[
        {
          id:'1',
          name: 'Galleta',
          price: '3.58',
          description: 'Galleta rellena de chocolate',
          thumbnailLink: 'https://cdn7.kiwilimon.com/recetaimagen/3329/640x426/th5-640x426-38990.jpg.webp'
        },
        {
          id:'2',
          name: 'Galletita',
          price: '3.58',
          description: 'Galletatita rellena de chocolate',
          thumbnailLink: 'https://cdn7.kiwilimon.com/recetaimagen/3329/640x426/th5-640x426-38990.jpg.webp'
        }
      ]
    }
  }
};
</script>

<style>
.posts-page{
    display:flex;
    justify-content: center;
    align-items: center;
}
</style>