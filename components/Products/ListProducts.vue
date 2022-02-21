<template>
    <section>
        <div class="row">
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
    </section>
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
