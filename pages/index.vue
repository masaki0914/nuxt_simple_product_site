<template>
  <div>
    <section class="jumbotron text-center">
      <div class="container">
        <h1 class="jumbotron-heading">キカガクの商品紹介サイト</h1>
        <p class="lead text-muted">
          短期のハンズオンセミナーや長期コースなど様々な講座を用意しています。
        </p>
        <p>
          <a href="https://www.kikagaku.co.jp/" class="btn btn-primary my-2">
            キカガクのホームページ
          </a>
        </p>
      </div>
    </section>
    <main>
      <div class="album py-5">
        <div class="container">
          <div class="row">
            <!-- 商品カード -->
            <ProductCard 
             v-for="(product, index) in products"
             :key="index"
             :name="product.name"
             :img="product.img"
             :text="product.text"
             :url="products.url"
            />
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
  import axios from 'axios'
  export default {
    async asyncData() {
      const url = 'https://api.steinhq.com/v1/storages/616d044dc582292380ab0c35/product'
      const { data } = await axios.get(url)
      return { products: data }
    },
  }
</script>
