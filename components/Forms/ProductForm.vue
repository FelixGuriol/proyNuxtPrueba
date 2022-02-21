<template>
    <form @submit.prevent="onSave">
        <AppControlInput v-model="editedProduct.name">Nombre de Producto</AppControlInput>

        <AppControlInput v-model="editedProduct.price">Precio</AppControlInput>
                
        <AppControlInput v-model="editedProduct.thumbnailLink">Link de miniatura</AppControlInput>
                
        <AppControlInput
                control-type="textarea"
                v-model="editedProduct.description">Descripcion</AppControlInput>
        <!-- <div>
            <p>Category:</p>
            <select name="category" id="category">
                <option value="1">Chatarra</option>
                <option value="2">Natural</option>
            </select>
        </div> -->
                
        <AppButton type="submit">Save</AppButton>
                
        <AppButton
                type="button"
                style="margin-left: 10px"
                btn-style="cancel"
                @click="onCancel">Cancel</AppButton>
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