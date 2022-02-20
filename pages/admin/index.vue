<template>
    <div class="admin-page">
        <section class="new-post">
            <AppButton @click="$router.push('/admin/new-product')">Crear Producto</AppButton>
            <AppButton style="margin-left: 10px"  @click="onLogout">Cerrar sesion</AppButton>
        </section>
        <section class="existing-posts">
            <h1>Productos:</h1>
            <ListProducts :products="loadedProducts" isAdmin/>
        </section>
    </div>
</template>

<script>
import ListProducts from '@/components/Products/ListProducts'
import AppButton from '@/components/UI/AppButton'

export default {
    layout:'admin',
  components: {
    ListProducts,
    AppButton
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
  },
  methods:{
    onLogout(){
      //this.$store.dispatch('logout');
      this.$router.push('/admin/auth')
    }
  }
/*   computed:{
    loadedPosts(){
      return this.$store.getters.loadedPosts
    }
  } */
}
</script>

<style scoped>
.admin-page {
  padding: 20px;
}

.new-post {
  text-align: center;
  border-bottom: 2px solid #ccc;
  padding-bottom: 10px;
}

.existing-posts h1 {
  text-align: center;
}
</style>