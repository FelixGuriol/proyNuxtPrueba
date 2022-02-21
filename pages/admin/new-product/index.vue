<template>
    <div class="admin-new-post-page">
        <section class="new-post-form">
            <ProductForm @submit="onSubmitted" />
        </section>

    </div>
</template>

<script>
import axios from 'axios'//se tiene q instalar npm install --save axios
import ProductForm from '@/components/Forms/ProductForm';
export default {
    layout:'admin',
    middleware: ['check-auth','auth'],
    components:{
        ProductForm
    },
    methods: {
      onSubmitted(productData){
        //console.log(postData);
        this.$store.dispatch('addPost', productData).then(()=>{
          this.$router.push('/admin');
          //console.log(postData);
        })
      }
    }
}
</script>

<style scoped>
.new-post-form {
  width: 90%;
  margin: 20px auto;
}

@media (min-width: 768px) {
  .new-post-form {
    width: 500px;
  }
}
</style>