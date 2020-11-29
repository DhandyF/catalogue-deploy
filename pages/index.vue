<template>
  <div class="catalog-container">
    <div class="search-bar">
      <input type="text" placeholder="Search product" name="search">
    </div>
    <div class="product">
      <div v-for="i in 7" :key="i" class="product-card">
        <img class="product-image" src="~/assets/images/kaos-polos1.jpg" alt="kaos polos">
        <div class="product-attr">
          <div class="product-name">
            Kaos Polos Screamous
          </div>
          <div class="product-price">
            Rp.30.000
          </div>
        </div>
      </div>
    </div>
    <transition name="home">asd</transition>
  </div>
</template>

<script>
export default {
  layout: 'catalog',
  transition: 'home'
}
</script>

<style>
.home-enter-active, .home-leave-active {
  transition: opacity .5s;
}

.home-enter, .home-leave-active {
  opacity: 0;
}

.catalog-container {
  margin: 0 auto;
  display: flex;
  flex-direction: column;
}

.search-bar {
  width: 100%;
  margin: 0 0 30px 0;
  /* border: 1px solid green; */
}

.search-bar input {
  width: 100%;
  padding: 5px 10px;
  font-size: 15px;
  font-family: 'Quicksand', sans-serif;
  border: 1px solid lightgrey;
  border-radius: 20px;
}

.search-bar input:focus{
  outline: none;
}

.search-bar i {
  font-size: 15px;
  background-image: url('~assets/icons/search.svg');
  display: inline-block;
  width: 20px;
  height: 20px;
  border: 1px solid lightgrey;
  /* border-radius: 0 5px 5px 0; */
  background-size: 20px 20px;
}

.product {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  justify-content: left;
}

.product-card {
  width: 180px;
  height: 300px;
  margin: 6px;
  padding: 0;
  display: flex;
  flex-direction: column;
  border-radius: 10px;
  box-shadow: 0px 0px 5px 0px rgba(0,0,0,0.2);
  cursor: pointer;
  /* border: 1px solid grey; */
}

.product-card:hover {
  box-shadow: 0px 0px 10px 0px rgba(0,0,0,0.5);
}

.product-card .product-image {
  width: 100%;
  height: 170px;
  margin: 0;
  padding: 0;
  border-radius: 10px 10px 0 0;
}

.product-card .product-attr {
  margin: 0;
  padding: 10px;
}

.product-attr .product-name {
  margin: 0 0 10px 0;
  font-family: 'Quicksand-SemiBold', sans-serif;
  color: darkslategrey;
  font-size: 17px;
}

.product-attr .product-price {
  font-family: 'Quicksand-Bold', sans-serif;
  color: #FA591D;
  font-size: 18px;
}
</style>
