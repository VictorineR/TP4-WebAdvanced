<template>
  <div>
    <h2>Mon Panier</h2>
    <article v-for="article in panier.articles" :key="article.id">
      <div class="article-content">
        <h3>Id: {{ article.id }} - Quantity: {{ article.quantity }} </h3>
        <input type="number" v-model="quantity" placeholder="Quantity" required/>
        <button @click="putInPanier(article.id, quantity)">Change quantity</button>
      </div>
    
    </article>
  </div>
</template>

<script>
module.exports = {
  props: { 
    articles: { type: Array, default: [] },
    panier: { type: Object }
  },
  data () {
    return {
    }
  },
  async mounted () {
  },
  methods: {
    putInPanier(articleId, articleQuantity) {
      this.$emit("put-in-panier", articleId,articleQuantity);
    },
  }
}
</script>

<style scoped>
h2{
  justify-content: space-around;  
  text-align: center;
  font-size: 25px;
  text-align: flex;
  color: rgb(161, 56, 7);
  
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
  
}


</style>
