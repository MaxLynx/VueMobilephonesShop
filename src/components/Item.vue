<template>
  <div class="item">
    <h3>{{phone.productName}}</h3>
    <img :src="getImageSrc(phone)" alt="Image not found"/>
    <p>{{phone.brandName.toUpperCase()}}</p>
    <p><b>OS: {{phone.operationSystem}}</b></p>
    <p><b>Cards: {{phone.numSimCard}}</b></p>
    <p id="price">{{phone.priceUAH.substr(0, 1) + " " 
                        + phone.priceUAH.substr(1) + " ₴"}}</p>
    <button class="availableBuyButton" v-if="phone.countProducts > 0"
        v-on:click="addToBasket(phone.id)">BUY NOW</button>
    <button class="unavailableBuyButton" v-if="phone.countProducts <= 0"
        >NOT AVAILABLE</button>
  </div>
</template>

<script>

export default {
  name: 'Item',
  
  props: ['phone'],

  methods: {
			getImageSrc(phone) {
        return "http://apeps.kiev.ua/images/phones/" + phone.id + ".jpg";
      },
      addToBasket(id) {
            for(let i = 0; i < this.$parent.$parent.phones.length; i++){
              if(this.$parent.$parent.phones[i].id == id){
                this.$parent.$parent.phones[i].purchasedCount++;
                this.$parent.$parent.phones[i].countProducts--;
              }
            }
          
        
      }
  }
}
</script>
<style>
  .item {
    border: 2px solid lightblue;
    border-radius: 20px;
  }

  .item img {
    display: block;
    margin-left: auto;
    margin-right: auto;
  }

  .item button {
    display: block;
    margin-left: auto;
    margin-right: auto;
    height: 3em;
    margin-bottom: 10px;
    border: 0;
    border-radius: 4px;
    color: white;
  }

  .availableBuyButton {
    background-color: darkgreen;
  }

  .unavailableBuyButton {
    background-color: rgb(216, 108, 117);
  }

  .item p {
    text-align: center;
    font-size: 1em;
    margin: 5px;
  }

  #price {
    color: purple;
    font-size: 2.5em;
  }
</style>