<template>
    <nuxt-link :to="productLink">
        <!--max-w-sm: hace q el card tenga dimensiones estaticas-->
        <div class="card bg-white">
            <img class="w-full" :src="thumbnail">
            <div class="px-6 py-4">
                <div class="font-bold text-xl mb-2">
                    {{name}} - S/. {{price}}
                </div>
                <p class="text-gray-700 text-left">
                    {{description}}
                </p>
            </div>
            <div class="px-6 py-4 flow-root">
                <span class="category">#{{nameCategory}}</span>
            </div>
        </div>
        <!-- <article>
            <div class="post-thumbnail" :style="{backgroundImage: 'url('+thumbnail+')'}" ></div>
            <div class="post-content">
                <h1>{{name}} - S/. {{price}}</h1>
                <p>{{description}} - {{nameCategory}}</p>
            </div>
        </article> -->
    </nuxt-link>
</template>
<!-- <template>
    <div class="w-full sm:w-1/2 md:w-1/3 px-2">
        <div class="card bg-white">
            <img class="w-full" :src="thumbnail">
            <div class="px-6 py-4">
                <div class="font-bold text-xl mb-2">
                    {{name}} - S/. {{price}}
                </div>
                <p class="text-gray-700 text-left">
                    {{description}}
                </p>
            </div>
            <div class="px-6 py-4 flow-root">
                <span class="category">#{{nameCategory}}</span>
            </div>
        </div>
    </div>
</template>-->

<script>
export default {
    name: 'Product',
    props:{
        id:{
            type: String,
            required: true
        },
        isAdmin:{
            type: Boolean,
            required: true
        },
        name:{
            type: String,
            required: true
        },
        price:{
            type: String,
            required: true
        },
        description:{
            type: String,
            required: true
        },
        thumbnail:{
            type: String,
            required: true
        },
        nameCategory:{
            type: String,
            required: true
        }
    },
    computed:{
        productLink(){
            return this.isAdmin ? '/admin/' + this.id : '/products/' +this.id
        }
    }
}
</script>
<!--
<style scoped>
.post-preview {
  border: 1px solid #ccc;
  box-shadow: 0 2px 2px #ccc;
  background-color: white;
  width: 90%;
}

a {
  text-decoration: none;
  color: black;
}

@media (min-width: 850px) {
  .post-preview {
    width: 400px;
    margin: 10px;
  }
}

.post-thumbnail {
  width: 100%;
  height: 200px;
  background-position: center;
  background-size: cover;
}

.post-content {
  padding: 10px;
  text-align: center;
}

a:hover .post-content,
a:active .post-content {
  background-color: #ccc;
}
</style>-->