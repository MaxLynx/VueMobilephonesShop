<template>
  <div class="bag">
    <button id="showBagButton" v-on:click="show = !show">
      YOUR BAG
    </button>
    <transition name="fade">
      <div v-if="show">
        <Purchase
          v-if="show"
          v-for="phone in phones"
          :key="phone.id"
          :phone="phone"
		    />
        <strong>Total: {{total}}</strong>
      </div>
    </transition>
    
  </div>
</template>

<script>
import Purchase from './Purchase';

export default {
  name: 'Bag',
  
  components: {
    Purchase
  },

  props: ['phones', 'show'],

  computed: {
    total: function(){
      let total = 0;
      for(let i = 0; i < this.$parent.phones.length; i++){
              total += this.$parent.phones[i].purchasedCount * this.$parent.phones[i].priceUAH;
            }
      return total;
    }
  },

  data: {
    show: true
  }

}
</script>
<style>
  .bag {
    text-align: left;
    margin-bottom: 20px;
  }
  .fade-enter-active, .fade-leave-active {
    transition: opacity .5s;
  }
  #showBagButton {
     width: 18em;
     height: 3em;
     display:inline-block;
     padding:0.35em 1.2em;
     border:0.1em solid #FFFFFF;
     margin:0 0.3em 0.3em 0;
     border-radius:0.12em;
     box-sizing: border-box;
     text-decoration:none;
     font-family:'Roboto',sans-serif;
     font-weight:300;
     font-size: 2em;
     color:blue;
     text-align:center;
     transition: all 0.2s;
  }
  #showBagButton:hover{
     color:#000000;
  }
</style>