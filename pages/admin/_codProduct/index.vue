<template>
    <div class="admin-post-page">
        <section class="update-form">
            <ProductForm :product="loadedProduct" @submit="onSubmitted" />
        </section>
    </div>
</template>

<script>
import ProductForm from '@/components/Forms/ProductForm';

export default {
    layout:'admin',
    middleware: ['check-auth','auth'],
    components:{
        ProductForm
    },
/*     data(){
        return{
            loadedProduct:{
                id: this.$route.params.codProduct,
                name: 'Galleta',
                price: '3.58',
                description: 'Galleta rellena de chocolate',
                thumbnailLink: 'https://cdn7.kiwilimon.com/recetaimagen/3329/640x426/th5-640x426-38990.jpg.webp',
                category:{
                    id:'1',
                    name:'Chatarra'
                }
            }
        }
    }, */

    asyncData(context){
        //console.log(context.params)
        return context.app.$axios.$get('/products/'+
                        context.params.codProduct+
                        '.json')
        .then(data => {
            return {
                loadedProduct: {...data, id: context.params.codProduct}
            }
        })
        .catch(e => context.error(e))
    },
    methods:{
        onSubmitted(editedPost){
            this.$store.dispatch('editPost',editedPost).then(()=>{
                this.$router.push('/admin');
            });
        }
    }
    /*
    data(){
        return{
            loadedPost:{
                author: 'Felix',
                title: 'My awesome Post',
                content: 'Super amazing, thanks for that!',
                thumbnailLink: 'https://ecuador.unir.net/wp-content/uploads/2019/12/mba-tech.jpg'
            }
        }
    }
    */
}
</script>

<style scoped>
.update-form {
  width: 90%;
  margin: 20px auto;
}
@media (min-width: 768px) {
  .update-form {
    width: 500px;
  }
}
</style>