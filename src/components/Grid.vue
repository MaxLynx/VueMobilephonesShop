<template>
  <div class="grid">
    <Item
			v-for="phone in phones"
			:key="phone.id"
			:phone="phone"
		/>
  </div>
</template>

<script>
import Item from './Item';

export default {
  name: 'Grid',
  
  components: {
    Item
  },

  props: ['phones'],

}
</script>
<style>
  .grid {
    display: grid;
    grid-template-columns: auto auto auto auto;
    grid-column-gap: 72px;
    grid-row-gap: 50px;
  }
</style>