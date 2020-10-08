<template>
  <div>
    <h2>Mon Panier</h2>
    <article v-for="article in panier.articles" :key="article.id">
      <div class="article-content">
        <h3>{{article.quantity}} {{ articles.find(a => a.id === article.id).name }} | Prix total: {{ articles.find(a => a.id === article.id).price * article.quantity }}€</h3>
        <p>{{ articles.find(a => a.id === article.id).description }}</p>
      
        <input
          type="number"
          v-model="articleQuantity"
          placeholder="Quantité"
          required
        />
        <button @click="putInPanier(article.id, articleQuantity)">
          Changer la quantité
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
