<template>
  <div class="product-container">
    <div class="product-image">
      <div class="carousel">
        <div class="carousel-item fade">
          <div class="item-number">
            1/3
          </div>
          <img class="item-image" src="~/assets/images/kaos-polos.jpg" alt="test1">
        </div>
        <div class="carousel-item fade">
          <div class="item-number">
            2/3
          </div>
          <img class="item-image" src="~/assets/images/test-carousel2.jpg" alt="test2">
        </div>
        <div class="carousel-item fade">
          <div class="item-number">
            3/3
          </div>
          <img class="item-image" src="~/assets/images/test-carousel3.jpg" alt="test3">
        </div>
        <a class="prev-item" @click="plusSlide(-1)">&#10094;</a>
        <a class="next-item" @click="plusSlide(1)">&#10095;</a>
      </div>
      <div id="image-group">
        <img v-for="i in 7" :key="i" class="image" src="~/assets/images/kaos-polos.jpg" alt="kaos-polos">
        <a class="prev-image" @click="scrollLeft">&#10094;</a>
        <a class="next-image" @click="scrollRight">&#10095;</a>
        <!-- <span class="dot" @click="currentSlide(1)"></span>
        <span class="dot" @click="currentSlide(2)"></span>
        <span class="dot" @click="currentSlide(3)"></span> -->
      </div>
    </div>
    <div class="product-detail">
      <div class="product-name">
        Kaos Polos Screamous
      </div>
      <div class="product-price">
        <div class="label">
          Price
        </div>
        <div class="price">
          Rp. 30.000
        </div>
      </div>
      <div class="product-color">
        <div class="label">
          Color
        </div>
        <div class="color">
        </div>
      </div>
      <div class="product-desc">
        <div class="label">
          Description
        </div>
        <div class="desc">
          Cotton t-shirt
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  layout: 'product',
  data () {
    return {
      slideIndex: 1
    }
  },
  mounted () {
    this.showSlide(this.slideIndex)
  },
  methods: {
    showSlide (n) {
      const slides = document.getElementsByClassName('carousel-item')
      // const dots = document.getElementsByClassName('dot')
      if (n > slides.length) {
        this.slideIndex = 1
      }
      if (n < 1) {
        this.slideIndex = slides.length
      }
      for (let index = 0; index < slides.length; index++) {
        slides[index].style.display = 'none'
      }
      // for (let dotIndex = 0; dotIndex < dots.length; dotIndex++) {
      //   dots[dotIndex].className = dots[dotIndex].className.replace(' active', '')
      // }
      slides[this.slideIndex - 1].style.display = 'flex'
      // dots[this.slideIndex - 1].className += ' active'
    },
    plusSlide (n) {
      this.showSlide(this.slideIndex += n)
    },
    currentSlide (n) {
      this.slideIndex = n
      this.showSlide(n)
    },
    scrollRight () {
      const imgElement = document.getElementById('image-group')
      // imgElement.scrollLeft += 50
      let scrollAmount = 0
      const slideTimer = setInterval(function () {
        imgElement.scrollLeft += 20
        scrollAmount += 10
        if (scrollAmount >= 100) {
          window.clearInterval(slideTimer)
        }
      }, 25)
    },
    scrollLeft () {
      const imgElement = document.getElementById('image-group')
      // imgElement.scrollLeft -= 50
      let scrollAmount = 0
      const slideTimer = setInterval(function () {
        imgElement.scrollLeft -= 20
        scrollAmount += 10
        if (scrollAmount >= 100) {
          window.clearInterval(slideTimer)
        }
      }, 25)
    }
  }
}
</script>

<style scoped>
* {
  box-sizing: border-box;
}

.product-container {
  width: 100%;
  margin: 0;
  display: flex;
  /* border: 1px solid blue; */
}

.product-container .product-image {
  width: 40%;
  min-width: 250px;
  /* border: 1px solid blue; */
}

.product-container .product-detail {
  width: 60%;
  padding: 0 0 0 50px;
  display: flex;
  flex-direction: column;
  /* border: 1px solid yellow; */
}

.product-name {
  width: 100%;
  padding: 24px 0;
  font-family: 'Quicksand-Bold', sans-serif;
  font-size: 20px;
  color: #5c4050;
  border-bottom: 1px solid lightgrey;
}

.product-price, .product-color, .product-desc {
  width: 100%;
  padding: 20px 0;
  display: flex;
  border-bottom: 1px solid lightgrey;
}

.label {
  width: 120px;
  font-family: 'Quicksand-SemiBold', sans-serif;
  font-size: 15px;
  color: rgba(92, 64, 80, .5);
}

.price {
  font-family: 'Quicksand-Bold', sans-serif;
  color: #FA591D;
  font-size: 28px;
}

.desc {
  font-family: 'Quicksand-SemiBold', sans-serif;
  font-size: 15px;
  color: #5c4050;
}

.carousel {
  max-width: 1000px;
  height: 400px;
  position: relative;
  margin: auto;
  border-radius: 5px;
  box-shadow: 0px 0px 5px 0px rgba(0,0,0,0.2);
}

.carousel-item {
  display: none;
  width: 100%;
  height: 100%;
  justify-content: center;
  align-items: center;
  background-color: white;
  border-radius: inherit;
}

.item-number {
  color: #f2f2f2;
  font-size: 12px;
  padding: 8px 12px;
  position: absolute;
  top: 0;
}

.item-image {
  width: 100%;
  height: 100%;
  border-radius: inherit;
}

#image-group {
  display: flex;
  align-items: center;
  overflow: scroll;
  transform: 500ms ease 0s;
  position: relative;
  width: 100%;
  height: 140px;
  padding: 20px;
  margin: 0;
}

::-webkit-scrollbar{
  display: none;
}

.image {
  width: 80px;
  height: 80px;
  margin: 0 5px;
  padding: 5px;
  border-radius: 10px;
  box-shadow: 0px 0px 5px 0px rgba(0,0,0,0.2);
}

.image:hover {
  cursor: pointer;
  box-shadow: 0px 0px 5px 0px rgba(0,0,0,0.5);
}

.prev-item, .next-item {
  cursor: pointer;
  position: absolute;
  top: 50%;
  width: auto;
  margin-top: -22px;
  padding: 10px 18px;
  color: white;
  font-weight: bold;
  font-size: 20px;
  transition: 0.6s ease;
  border-radius: 50px;
  -moz-user-select: none;
  -webkit-user-select: none;
  background-color: rgba(0, 0, 0, 0.2);
}

.prev-item:hover, .next-item:hover {
  background-color: rgba(92, 64, 80, 1);
}

.next-item {
  right: 0;
  border-radius: 50px;
}

.prev-image, .next-image {
  cursor: pointer;
  position: sticky;
  width: auto;
  /* margin-top: -22px; */
  padding: 8px 16px;
  color: white;
  font-weight: bold;
  font-size: 20px;
  transition: 0.6s ease;
  border-radius: 50px;
  -moz-user-select: none;
  -webkit-user-select: none;
  background-color: rgba(92, 64, 80, .5);
}

.prev-image:hover, .next-image:hover {
  background-color: rgba(92, 64, 80, 1);
}

.prev-image {
  right: 400px;
}

.next-image {
  right: 0;
}

.fade {
  animation-name: fade;
  animation-duration: 1.5s;
}

.dot {
  cursor: pointer;
  height: 15px;
  width: 15px;
  margin: 0 2px;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
  transition: background-color 0.6s ease;
}

.active, .dot:hover {
  background-color: #717171;
}

@-webkit-keyframes fade {
  from {opacity: .4}
  to {opacity: 1}
}

@keyframes fade {
  from {opacity: .4}
  to {opacity: 1}
}
</style>
