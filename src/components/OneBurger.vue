<template>
  <div class="burger">
    <h3> {{ burger.name }} </h3>
    <img class="pics" v-bind:src="burger.img">
    <span id="ingredients">
      <ul>
        <li> {{ burger.calories }} </li>
        <li v-if="burger.lactose">Contains Lactose</li>
        <li v-else>Lactose Free</li>
        <li v-if="burger.gluten">Contains Gluten</li>
        <li v-else>Gluten Free</li>
        <li>{{ burger.price }}</li>
      </ul>
    </span>
    {{ amountOrdered }}
    <button type="submit" v-on:click="decrease()">
      -
    </button>
    <button type="submit" v-on:click="increase()">
      +
    </button>
    <button type="submit" v-on:click="addBurger()">
      Add to cart
    </button>
  </div>
</template>
  
<script>
export default {
  name: 'OneBurger',
  props: {
    burger: Object
  },
  data: function () {
    return {
      amountOrdered: 0
    }
  },
  methods: {
    decrease: function () {
      if (this.amountOrdered != 0) {
        this.amountOrdered -= 1;
      }
    },
    increase: function () {
      this.amountOrdered += 1;
    },
    addBurger: function () {
      this.$emit('orderedBurger', {
        name: this.burger.name,
        amount: this.amountOrdered
      }
      );
    }
  }
}
</script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.burger {
  color: darksalmon;
  border: 3px dotted pink;
  border-radius: 25px;
  padding: 5%
}

#ingredients {
  color: indianred;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  font-size: 10pt;
}

.pics {
  max-width: 280px;
  max-height: 200px;
  border: 1px solid pink;
  border-radius: 15px;
}

@media screen and (max-width: 1100px) {
  .pics {
    max-width: 200px;
    max-height: 100px;
  }
}
</style>
  