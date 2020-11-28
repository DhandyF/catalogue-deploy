<template>
  <div>
    <nav-bar />
    <div class="container">
      <div class="content">
        <div class="sidebar">
          <p>Filter</p>
        </div>
        <div class="catalog">
          <Nuxt />
        </div>
      </div>
    </div>
  </div>
</template>

<style>
html {
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

.container {
  width: 100%;
  margin: 60px 0 0 0;
  padding: 0 70px;
}

.content {
  width: 100%;
  margin: 0;
  padding: 0;
  display: flex;
  /* border: 1px solid black; */
}

.sidebar {
  width: 240px;
  /* border: 1px solid black; */
}

.catalog {
  width: 100%;
  margin: 0;
  padding: 20px;
  /* border: 1px solid yellow; */
}

.button--purple {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #5c4050;
  color: #5c4050;
  text-decoration: none;
  padding: 10px 30px;
}

.button--purple:hover {
  color: #fff;
  background-color: #5c4050;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}
</style>
