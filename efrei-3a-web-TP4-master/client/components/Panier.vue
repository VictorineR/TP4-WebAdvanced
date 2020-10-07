<template>
  <div>
    <h2>Mon Panier</h2>
    <ul v-for="article in panier.articles" :key="article.id">
      <li>Id: {{ article.id }} - Quantity: {{ article.quantity }} </li>
    </ul>
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
  }
}
</script>

<style scoped>
</style>
