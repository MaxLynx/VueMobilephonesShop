<template>
  <div class="purchase" v-if="phone.purchasedCount > 0">
    <span id="text">
    {{phone.productName}}: x{{phone.purchasedCount}}   ₴{{phone.purchasedCount * phone.priceUAH}}
    </span>
    <button class="cancelBuyButton"
        v-on:click="removeFromBag(phone.id)">CANCEL</button>
  </div>
</template>

<script>
export default {
  name: 'Purchase',
  
  props: ['phone'],

  methods: {
    removeFromBag(id) {
          for(let i = 0; i < this.$parent.$parent.phones.length; i++){
              if(this.$parent.$parent.phones[i].id == id){
                this.$parent.$parent.phones[i].purchasedCount--;
                this.$parent.$parent.phones[i].countProducts++;
              }
            }
    }
  }
}
</script>
<style>
  #text {
    color: orangered;
    font-weight: bold;
  }
  button {
    background-color: bisque;
    color: indigo;
    border-radius: 20px;
  }
</style>