<template>
  <div id="orders">
    <div id="orderList">
      <div v-for="(order, key) in orders" v-bind:key="'order' + key">
        Order
        # {{ key }}:
        <ul>
          <li v-for="(item, itemKey) in order.orderItems" :key="itemKey">
            {{ itemKey }}: {{ item }}
          </li>
        </ul>
        <div>
          Customer Information:
          {{ order.deliveryInformation.name }}
          {{ order.deliveryInformation.email }}
          {{ order.deliveryInformation.pm }}
          {{ order.deliveryInformation.gender }}
          <hr>
        </div>
      </div>
      <button v-on:click="clearQueue">Clear Queue</button>
    </div>
    <div id="dots" v-bind:style="{ background: 'url(' + require('../../public/img/polacks.jpg') + ')' }">
      <div v-for="(order, key) in orders" v-bind:style="{ left: order.details.x + 'px', top: order.details.y + 'px' }"
        v-bind:key="'dots' + key">
        {{ key }}
      </div>
    </div>
  </div>
</template>
<script>
import io from 'socket.io-client'
const socket = io();

export default {
  name: 'DispatcherView',
  data: function () {
    return {
      orders: null,
      accept: true,
      preparation: true,
    }
  },
  created: function () {
    socket.on('currentQueue', data =>
      this.orders = data.orders);
  },
  methods: {
    clearQueue: function () {
      socket.emit('clearQueue');
    }
  }
}
</script>
<style>
#orderList {
  top: 1em;
  left: 1em;
  position: absolute;
  z-index: 2;
  color: black;
  background: rgba(255, 255, 255, 0.5);
  padding: 1em;
  font-family: 'Times New Roman', Times, serif;
  font-style: oblique;
  width: 70%;
}

#dots {
  position: relative;
  margin: 0;
  padding: 0;
  background-repeat: no-repeat;
  width: 1920px;
  height: 1078px;
  cursor: crosshair;
}

#dots div {
  position: absolute;
  background: black;
  color: white;
  border-radius: 10px;
  width: 20px;
  height: 20px;
  text-align: center;
}

</style>
  