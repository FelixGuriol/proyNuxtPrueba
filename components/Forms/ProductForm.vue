<template>
<!-- <div>
            <p>Category:</p>
            <select name="category" id="category">
                <option value="1">Chatarra</option>
                <option value="2">Natural</option>
            </select>
        </div> -->
                
    <form @submit.prevent="onSave">
        <!-- <AppControlInput v-model="editedProduct.name">Nombre de Producto</AppControlInput>

        <AppControlInput v-model="editedProduct.price">Precio</AppControlInput>
                
        <AppControlInput v-model="editedProduct.thumbnailLink">Link de miniatura</AppControlInput>
                
        <AppControlInput
                control-type="textarea"
                v-model="editedProduct.description">Descripcion</AppControlInput>
        
        <AppButton type="submit">Save</AppButton>
                
        <AppButton
                type="button"
                style="margin-left: 10px"
                btn-style="cancel"
                @click="onCancel">Cancel</AppButton> -->
        <div class="container mx-auto">
            <div class="max-w-xl mx-auto divide-y">
                <div class="py-12">
                    <h2 class="text-2xl font-bold">Crear producto</h2>
                    <div class="mt-8">
                        <div class="grid grid-cols-1 gap-6">
                            <label class="block">
                                <span class="text-gray-700">Nombre del producto</span>
                                <input type="text" class="mt-1 block w-full" v-model="editedProduct.name">
                            </label>
                            <label class="block">
                                <span class="text-gray-700">Precio</span>
                                <input type="text" class="mt-1 block w-full" v-model="editedProduct.price">
                            </label>
                            <label class="block">
                                <span class="text-gray-700">Link de miniatura</span>
                                <input type="text" class="mt-1 block w-full" v-model="editedProduct.thumbnailLink">
                            </label>
                            <label class="block">
                                <span class="text-gray-700">Descripcion</span>
                                <textarea class="mt-1 block w-full" rows="3" v-model="editedProduct.description"></textarea>
                            </label>
                            <div class="bloc flex flex-wrap">
                                <AppButton type="submit">Save</AppButton>
                                    
                                <AppButton
                                        type="button"
                                        btn-style="cancel"
                                        @click="onCancel">Cancel</AppButton>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </form>
</template>

<script>
import AppButton from '@/components/UI/AppButton'
import AppControlInput from '@/components/UI/AppControlInput'

export default {
    components: {
        AppButton,AppControlInput
    },
    props:{
        product:{
            type: Object,
            required: false
        }
    },
    data(){
        return{
            editedProduct: this.product
            ? {...this.product}//si this.post existe, saca toda la data y su estructura y la guarda en editedPost
            : {//si this. post no existe crea un objeto vacio
                name:'',
                price:'',
                thumbnailLink:'',
                description:'',
                category:{
                    id:'1',
                    name:'Chatarra'
                }
            }
        }
    },
    methods:{
        onSave(){
            //Save the post
            //console.log(this.editedProduct);
            this.$emit('submit',this.editedProduct)
        },
        onCancel(){
            //Navigate back
            this.$router.push('/admin');
        }
    }
}
</script>