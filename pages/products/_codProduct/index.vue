<template>
    <div class="single-post-page">
        <section class="post">
            <h1 class="post-title">{{loadedProduct.name}}</h1>
            <div class="posts-details">
                <div class="post-detail">Last updated on {{loadedProduct.updatedDate}}</div>
                <div class="post-detail">Price: {{loadedProduct.price}}</div>
            </div>
            <p class="post-content">It's a type of {{loadedProduct.category.name}} and {{loadedProduct.description}}</p>
        </section>
        <section class="post-feedback">
            <p>Let me know what you think about the post, send a mail to <a href="mailto:feedback@gmail.com">feedback@gmail.com</a>.</p>
        </section>
    </div>
</template>

<script>
export default {
  asyncData(context){
    return context.app.$axios.$get('/products/'+context.params.codProduct+'.json')
      .then(data => {
        if(data===null){// el === es para el tipo de dato
          throw new Error()
        }
        return {
          loadedProduct: data
        }
      })
      .catch(e => context.error(e))
  },
  head:{// sobre escribe el head de nuxt.config.js
    title: 'A free product'
  }
}
</script>

<style>
.single-post-page {
  padding: 30px;
  text-align: center;
  box-sizing: border-box;
}

.post {
  width: 100%;
}

@media (min-width: 768px) {
  .post {
    width: 600px;
    margin: auto;
  }
}

.post-title {
  margin: 0;
}

.post-details {
  padding: 10px;
  box-sizing: border-box;
  border-bottom: 3px solid #ccc;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

@media (min-width: 768px) {
  .post-details {
    flex-direction: row;
  }
}

.post-detail {
  color: rgb(88, 88, 88);
  margin: 0 10px;
}

.post-feedback a {
  color: red;
  text-decoration: none;
}

.post-feedback a:hover,
.post-feedback a:active {
  color: salmon;
}
</style>