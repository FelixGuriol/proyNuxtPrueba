<!--
<template>
    <nuxt-link :to="productLink" class="post-preview">
        <article>
            <div class="post-thumbnail" :style="{backgroundImage: 'url('+thumbnail+')'}" ></div>
            <div class="post-content">
                <h1>{{name}} - S/. {{price}}</h1>
                <p>{{description}} - {{nameCategory}}</p>
            </div>
        </article>
    </nuxt-link>
</template>
-->
<template>
    <div class="col-12 col-sm-6 col-md-3">
        <nuxt-link :to="productLink">
            <div class="card" style="margin-bottom: 15px !important;">
                <div class="post-thumbnail" :style="{backgroundImage: 'url('+thumbnail+')'}" ></div>
                <div class="card-body">
                    <h5 class="card-title">{{name}} - S/. {{price}}</h5>
                    <p class="card-text">{{description}} - {{nameCategory}}</p>
                </div>
            </div>
        </nuxt-link>
    </div>
</template>

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

<style scoped>
a:link, a:visited, a:active {
    text-decoration:none !important;
    color: black;
}
.post-thumbnail {
  width: 100%;
  height: 200px;
  background-position: center;
  background-size: cover;
}

</style>