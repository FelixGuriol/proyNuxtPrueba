<template>
    <div class="container mx-auto">
        <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-4 mx-2">
            <Product
                v-for="product in products"
                :key="product.id"

                :id="product.id"
                :is-admin="isAdmin"
                :name="product.name"
                :price="product.price"
                :description="product.description"
                :thumbnail="product.thumbnailLink"
                :nameCategory="product.category.name"
            />
        </div>
        <!-- <div class="flex -mx-2 flex-wrap">
                <Product
                    v-for="product in products"
                    :key="product.id"

                    :id="product.id"
                    :is-admin="isAdmin"
                    :name="product.name"
                    :price="product.price"
                    :description="product.description"
                    :thumbnail="product.thumbnailLink"
                    :nameCategory="product.category.name"
                />
        </div> -->
    </div>
    
    
    <!-- <section>
        
    </section> -->
</template>

<script>
import Product from "@/components/Products/Product";

export default {
    components:{
        Product

    },
    props:{
        isAdmin:{
            type: Boolean,
            default: false
        },
        products:{
            type: Array,
            required: true
        }
    },
/*     created(){
        console.log('------------');
        console.log(this.products);
        console.log('------------');
    } */
}
</script>
<!--
<style scoped>
.post-list{
  display: flex;
  padding: 20px;
  box-sizing: border-box;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
}
</style>-->