<template>
  <div>
    <h2>Mon Panier</h2>
    <article v-for="article in panier.articles" :key="article.id">
      <div class="article-content">
        <div class="article-img">
          <div
            :style="{
              backgroundImage:
                'url(' + articles.find((a) => a.id === article.id).image + ')',
            }"
          ></div>
        </div>
        <h3>
          {{ article.quantity }}
          {{ articles.find((a) => a.id === article.id).name }} | Prix total:
          {{
            articles.find((a) => a.id === article.id).price * article.quantity
          }}€
        </h3>
        <p>{{ articles.find((a) => a.id === article.id).description }}</p>

        <input
          type="number"
          v-model="article.articleQuantity"
          placeholder="Quantité"
        />
        <button @click="putInPanier(article.id, article.articleQuantity)">
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
    panier: { type: Object },
  },
  data() {
    return {
      articleQuantity: "",
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

h2{
  justify-content: space-around;  
  text-align: center;
  font-size: 25px;
 
  color: black;  
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
  
}

.article-content{
  display: center;
  text-align: center;
  padding: 40px;

}

.article-content h3{
  justify-content: space-around;  
  text-align: left;
  font-size: 25px;
  color: black;
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
  
}

.article-content p{
  justify-content: space-around;  
  text-align: left;
  font-size: 17px;
  color: black;
}

.article-img div {
  width: 120px;
  height: 120px;
  background-size: cover;
}

</style>
