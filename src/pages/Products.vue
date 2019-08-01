// pages/Products.vue
<template>
  <Layout>
    <h1>Products</h1>
    <div
      style="text-align: center"
      v-for="edge in $page.allContentfulProduct.edges"
      v-bind:key="edge.node.id"
    >
      <h2 style="margin-bottom: 0.25em">{{ edge.node.name }}</h2>
      <button
        class="snipcart-add-item cart-button"
        v-bind:data-item-id="edge.node.id"
        v-bind:data-item-name="edge.node.name"
        v-bind:data-item-image="edge.node.image.file.url"
        v-bind:data-item-price="edge.node.price"
        v-bind:data-item-url="edge.node.path"
      >Buy for ${{ edge.node.price}}</button>
      <g-image
        v-bind:src="edge.node.image.file.url"
        style="width: 100%; height: 300px; object-fit: contain;"
        v-bind:alt="edge.node.image.title"
      />
      <p>{{ edge.node.description }}</p>
    </div>
    <Pager v-bind:info="$page.allContentfulProduct.pageInfo" linkClass="pager" />
  </Layout>
</template>

<page-query>
query ($page: Int) {
  allContentfulProduct (perPage: 2, page: $page) @paginate {
    pageInfo {
      totalPages
      currentPage
    }
    edges {
      node {
        id
        path
        name
        price
        description
        image {
          title
          file {
            url
          }
        }
      }
    }
  }
}
</page-query>

<script>
import { Pager } from "gridsome";

export default {
  components: {
    Pager
  },
  metaInfo: {
    title: "Products",
    meta: [
      { charset: "utf-8" },
      { name: "author", content: "Gaylon Alfano" },
      {
        name: "description",
        content:
          "Discover our entire range of luxury apparel, shoes, and accessories."
      },
      {
        name: "keywords",
        content: "Premium Jackets, High-End Clothing, Designer Sunglasses"
      }
    ]
  }
};
</script>

<style>
.pager {
  font-style: 1.5rem;
  letter-spacing: 0.5px;
  padding: 40px 20px;
}

.cart-button {
  background-color: forestgreen;
  border: none;
  border-radius: 5px;
  color: white;
  padding: 8px 16px;
  margin-bottom: 10px;
  text-decoration: none;
  font-size: 1rem;
}
</style>
