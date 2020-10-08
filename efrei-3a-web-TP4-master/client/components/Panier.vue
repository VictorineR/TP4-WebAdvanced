<template>
  <div>
    <h2>Mon Panier</h2>
    <article v-for="article in panier.articles" :key="article.id">
      <div class="article-content">
        <h3>Id: {{ article.id }} - Name: {{ article.name }} - Quantity: {{ article.quantity }}</h3>
        <input
          type="number"
          v-model="articleQuantity"
          placeholder="Quantity"
          required
        />
        <button @click="putInPanier(article.id, articleQuantity)">
          Change quantity
        </button>
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
  data() {
    return {
      articleQuantity: ''
    };
  },
  async mounted() {},
  methods: {
    putInPanier(articleId, articleQuantity) {
      this.$emit("put-in-panier", articleId, articleQuantity);
    },
  },
};
</script>

<style scoped>
</style>
