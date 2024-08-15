<template>
  <div class="product-card">
    <div class="top-card">
      <div class="top-card__product-images">
        <div class="top-card__product-logo"></div>
        <div class="top-card__product-image"></div>
      </div>
      <h2 class="top-card__product-name">{{ product.name }}</h2>
      <h3 class="top-card__product-slogan">{{ product.slogan }}</h3>
      <div class="top-card__product-top">{{ product.top }}</div>
    </div>
    <div class="bottom-card">
      <div class="bottom-card__header">
        <h1 class="bottom-card__product-name">{{ product.name }}</h1>
        <div class="bottom-card__product-new" v-if="product.isNew">NEW</div>
      </div>

      <h2 class="bottom-card__product-category">{{ product.category }}</h2>

      <div class="bottom-card__stars">
        <div
          class="bottom-card__star--filled"
          v-for="i in product.rating"
          :key="`rating-${i}`"
        ></div>
        <div
          class="bottom-card__star"
          v-for="i in 5 - product.rating"
          :key="`rating-${5 - i}`"
        ></div>
      </div>

      <div class="bottom-card__sizes">
        <h3 class="bottom-card__sizes-header">РАЗМЕРЫ</h3>
        <div class="bottom-card__sizes-container">
          <div
            class="bottom-card__size"
            :class="{ 'bottom-card__size--selected': product.initialSize === size.id }"
            v-for="size in product.sizesArray"
            :key="`size-${size.id}`"
          >
            {{ size.value }}
          </div>
        </div>
      </div>

      <div class="bottom-card__colors">
        <h3 class="bottom-card__colors-header">ЦВЕТ</h3>
        <div class="bottom-card__colors-container">
        
          <div
            class="bottom-card__color"
            :class="{ 'bottom-card__color--selected': product.initialColor === color.id }"
            v-for="color in product.colorsArray"
            :style="{'background-color': color.color, 'outline-color': color.color}"
            :key="`color-${color.id}`"
          ></div>
        </div>
      </div>

      <div class="bottom-card__product-price">{{ product.price }}</div>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps(["product"]);
</script>

<style>
.product-card {
  position: relative;
  width: 280px;
  height: 510px;
  box-sizing: border-box;
  margin: auto;
  border-radius: 25px;
  box-shadow: -5px 5px 0 0 #eb7f4280;
}

.top-card {
  width: 100%;
  height: 255px;
  padding: 15px;
  background: linear-gradient(-45deg, #b93938, #eb7f42);
  border-top-right-radius: 25px;
  border-top-left-radius: 25px;
  box-sizing: border-box;
}

.top-card__product-images {
  display: flex;
  width: 100%;
  justify-content: space-between;
}

.top-card__product-logo {
  width: 47px;
  height: 27px;
  background-image: v-bind("props.product.logoLink");
  background-size: 100%;
}

.top-card__product-image {
  width: 120px;
  height: 121px;
  background-image: v-bind("props.product.imageLink");
  background-size: 100%;
}

.top-card__product-name {
  margin: 10px 0 0 0;
  color: white;
  font-size: 14px;
  font-weight: 650;
}

.top-card__product-slogan {
  margin-top: 5px;
  color: white;
  font-size: 12px;
  font-weight: 650;
}

.top-card__product-top {
  margin-top: -25px;
  margin-left: -17px;
  color: #2c3e5040;
  font-size: 110px;
  letter-spacing: -6px;
  font-weight: 650;
}

.bottom-card {
  padding: 40px 15px 15px 15px;
  height: 255px;
  border-right: 1px solid #eb7f4280;
  border-bottom: 1px solid #eb7f4280;
  border-bottom-right-radius: 25px;
  border-bottom-left-radius: 25px;
  box-sizing: border-box;
}

.bottom-card__header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.bottom-card__product-name {
  margin: 0;
  font-size: 20px;
  font-weight: 750;
}

.bottom-card__product-new {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 25px;
  width: 40px;
  background-color: #2cee6e;
  
  color: white;
  font-size: 13px;
  font-weight: 650;
  border-radius: 5px;
}

.bottom-card__product-category {
  margin-top: 5px;
  margin-bottom: 0;

  font-size: 12px;
  font-weight: 400;
}

.bottom-card__stars {
  margin-top: 7px;
  display: flex;
  gap: 5px;
}

.bottom-card__star,
.bottom-card__star--filled {
  width: 10px;
  height: 10px;
  background: url("../assets/star.svg");
  background-repeat: no-repeat;
  background-position: center;
}

.bottom-card__star--filled {
  background-image: url("../assets/star-filled.svg");
}

.bottom-card__sizes, .bottom-card__colors {
  margin-top: 15px;
}

.bottom-card__sizes-header, .bottom-card__colors-header {
  margin: 0;

  font-size: 12px;
  font-weight: 650;
}

.bottom-card__sizes-container {
  display: flex;
  margin-top: 15px;
  margin-left: -5px;
  gap: 12px;
}

.bottom-card__size {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 25px;
  height: 25px;
  border-radius: 50%;

  font-size: 12px;
  font-weight: 650;
  transition: all ease 0.2s;

  cursor: pointer;
}

.bottom-card__size:hover {
  background-color: lightgrey;
  transition: all ease 0.2s;
}

.bottom-card__size--selected {
  background-color: #EB7F42;
  color: white;
}

.bottom-card__size--selected:hover {
  background-color: #EB7F42;
}

.bottom-card__colors-container {
  display: flex;
  gap: 10px;
  margin-top: 15px;
}

.bottom-card__color {
  width: 15px;
  height: 15px;
  border-radius: 50%;
  border: 5px solid white;
  outline: 0px solid; 

  cursor: pointer;
  transition: all ease 0.1s;
}

.bottom-card__color--selected, .bottom-card__color:hover {
  outline: 1px solid;
  transition: all ease 0.1s;
}

.bottom-card__product-price {
  position: absolute;
  bottom: 12px;
  right: -10px;

  font-size: 20px;
  font-weight: 650;

  padding: 3px 9px;
  background: #2CEE6E;
  border-radius: 5px;
  color: white;
  cursor: pointer;
}
</style>
