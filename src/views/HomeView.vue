<template>
  <header id="header-container">
    <h1>Alice's Vego Burgers</h1>
    <img src="https://newcastlelive.com.au/wp-content/uploads/2022/07/burg-street-1.jpg" alt="Headerpic" title="Headerpic"
      id="headerpic">
  </header>
  <nav>
    <ul class="horizontal-menu">
      <li><a href="/">Home</a></li>
      <li><a href="javascript:void(0);" v-on:click="scrollToBurgerSection">Start your order</a></li>
      <li><a href="javascript:void(0);" v-on:click="scrollToContactSection">Contact</a></li>
    </ul>
  </nav>
  <main>
    <section class="burger" id="burger-section">
      <h2>Select Burger</h2>
      <p>Here you can start your order by selecting burgers according to your preferences!</p>
      <div class="wrapper">
        <Burger v-for="burger in burgers" v-bind:burger="burger" v-bind:key="burger.name"
          v-on:orderedBurger="addToOrder($event)" />
      </div>
    </section>
    <section class="customerinformation" id="customerinformation">
      <h2>Customer Information</h2>
      <h3>Delivery Information:</h3>
      <p>
        <label for="fullname">Full Name</label><br>
        <input type="text" id="fullname" v-model="fullname" required placeholder="First- and last name">
      </p>
      <p>
        <label for="email">E-mail</label><br>
        <input type="email" id="email" v-model="email" required placeholder="E-mail address">
      </p>
      <!-- <p>
        <label for="streetname">Street Name</label><br>
        <input type="text" id="streetname" v-model="streetname" required placeholder="Street name">
      </p>
      <p>
        <label for="housenumber">House Number</label><br>
        <input type="number" id="housenumber" v-model="housenumber" required placeholder="House number">
      </p> -->
      <div id="map-container">
        Click on the map to choose your delivery location:
        <div id="map" v-on:click="addOrder">
          <div id="dots">
            <div v-bind:style="{ left: location.x + 'px', top: location.y + 'px' }">T</div>
          </div>
        </div>
      </div>
      <h3>Choose your Payment Method:</h3>
      <p>
        <label for="payment">Payment Method</label>
        <select id="payment" v-model="payment">
          <option value="Card" selected>Card</option>
          <option value="Swish">Swish</option>
          <option value="Klarna">Klarna</option>
          <option value="Bank transfer">Bank transfer</option>
        </select>
      </p>
      <p>
      <form>
        <h3>Gender</h3>
        <input type="radio" id="female" v-model="gender" value="Female">
        <label for="female">Female</label>
        <input type="radio" id="male" v-model="gender" value="Male">
        <label for="male">Male</label>
        <input type="radio" id="nonbinary" v-model="gender" value="Nonbinary">
        <label for="nonbinary">Non-binary</label>
        <input type="radio" id="undisclosed" v-model="gender" value="Undisclosed">
        <label for="undisclosed">Undisclosed</label>
      </form>
      </p>
      <div id="orders">
        <button type="submit" v-on:click="markDone()" @click.prevent=notify>
          <img
            src="https://creazilla-store.fra1.digitaloceanspaces.com/emojis/47298/check-mark-button-emoji-clipart-xl.png"
            style="width: 12px;">
          Place my order!
        </button>
      </div>
      <section id="receipt" v-if="showReceipt">
        Thank you for ordering from Alice's Vego Burgers!
        <div>We have recieved your order <img
            src="https://creazilla-store.fra1.digitaloceanspaces.com/emojis/47298/check-mark-button-emoji-clipart-xl.png"
            style="width: 12px;"></div>
        <hr>
        <div>Here is your receipt:</div>
        <div v-for="(item, itemKey) in orderedBurgers" :key="itemKey">
          {{ itemKey }}: {{ item }} </div>
        <hr>
        <div> Total Cost: {{ totalCost }} SEK</div>
      </section>
    </section>
  </main>
  <hr>
  <footer id="footer">
    &copy; 2023 Alice's Vego Burgers Inc
    <div id="address">Address: Slottet, 752 37 Uppsala</div>
    <div id="phone">Phone: 31415926536</div>
  </footer>
</template>

<script>
import Burger from '../components/OneBurger.vue'
import io from 'socket.io-client'
import menu from '../assets/menu.json'

const socket = io();

//   function MenuItem(n, kcal, g, l){
//   this.name = n;
//   this.calories = kcal;
//   this.gluten = g;
//   this.lactose = l;
// }

// let allBurgers = [ {name: "Burger1", calories: 300, url: "https://www.max.se/contentassets/bd97342be78047eb8f8026452d545538/product_halloumiburgare2.png?width=1160&sharpen=5&sigma=1,4&threshold=0", lactose: false, gluten: true},
// {name: "Burger2", calories: 400, url: "https://www.max.se/contentassets/f5f13dcf34c24873878e030df544b066/product_delifresh-signature-plant-beef.png", lactose: true, gluten: true}, 
// {name: "Burger3", calories: 500, url: "https://www.max.se/contentassets/922794117dbc4b0ba03d50e419643a5b/68300_hemsida-produkt_friscocheese-plantbeef_c3_2023_1920x1787px_se-no-dk.png?width=1160&sharpen=5&sigma=1,4&threshold=0", lactose: false, gluten: false}
// ]

// console.log(allBurgers)

export default {
  name: 'HomeView',
  components: {
    Burger
  },
  data: function () {
    return {
      burgers: menu,
      fullname: '',
      email: '',
      streetname: '',
      housenumber: '',
      payment: '',
      gender: '',
      orderedBurgers: {},
      location: { x: 0, y: 0 },
      showReceipt: false,
      totalCost: 0,
    }
  },
  methods: {
    markDone: function () {
      if (this.fullname === '') {
        alert('You have not filled in all the necessary information');
      }
      else if (this.email === '') {
        alert('You have not filled in all the necessary information');
      }
      else if (this.payment === '') {
        alert('You have not filled in all the necessary information');
      }
      else if (this.gender === '') {
        alert('You have not filled in all the necessary information');
      }
      else if (Object.keys(this.orderedBurgers).length === 0) {
        alert('You have not selected any burgers');
      }
      else if (this.location.x === 0) {
        alert('You have not filled in all the necessary information')
      }
      else {
        this.calculateTotalCost(this.orderedBurgers);
        this.showReceipt = true;
        socket.emit("addOrder", {
          orderId: this.getOrderNumber(),
          details: {
            x: this.location.x,
            y: this.location.y
          },
          deliveryInformation: {
            name: this.fullname,
            email: this.email,
            gender: this.gender,
            pm: this.payment,
          },
          orderItems: this.orderedBurgers
        }
        );
      }
    },
    getOrderNumber: function () {
      return Math.floor(Math.random() * 10);
    },
    addOrder: function (event) {
      var offset = {
        x: event.currentTarget.getBoundingClientRect().left,
        y: event.currentTarget.getBoundingClientRect().top
      };
      // socket.emit("addOrder", {
      //   orderId: this.getOrderNumber(),
      //   details: {
      //     x: event.clientX - 10 - offset.x,
      //     y: event.clientY - 10 - offset.y
      //   },
      //   orderItems: ["Beans", "Curry"]
      // }
      // );
      this.location.x = event.clientX - 10 - offset.x;
      this.location.y = event.clientY - 10 - offset.y;
    },
    addToOrder: function (event) {
      this.orderedBurgers[event.name] = event.amount;
      console.log(this.orderedBurgers);
    },
    setLocation: function (event) {
      this.location.x = event.clientX - 10 - event.currentTarget.getBoundingClientRect().left;
      this.location.y = event.clientY - 10 - event.currentTarget.getBoundingClientRect().top;
      console.log(this.location);
    },
    scrollToBurgerSection() {
      const burgerSection = document.getElementById('burger-section');
      if (burgerSection) {
        burgerSection.scrollIntoView({ behavior: 'smooth' });
      }
    },
    scrollToContactSection() {
      const contactSection = document.getElementById('footer');
      alert('You can find our contact information at the bottom of this page')
      if (contactSection) {
        contactSection.scrollIntoView({ behavior: 'smooth' });
      }
    },
    calculateTotalCost: function (orderedBurgers) {
      this.totalCost = 0; // Resetting the totalCost to 0 before recalculating
      for (const burgerName in orderedBurgers) {
        if (orderedBurgers.hasOwnProperty(burgerName)) {
          const amount = orderedBurgers[burgerName];
          const burger = this.burgers.find(b => b.name === burgerName);
          // Check if the burger is found in the menu
          if (burger && burger.price) {
            // Increment the totalCost by the cost of the current burger multiplied by the amount
            this.totalCost += parseFloat(burger.price.replace(' SEK', '')) * amount; //Calculating the price, removing SEK (from price in json file)
          }
        }
      }
      console.log('Total Cost:', this.totalCost);
    }
  }
}
</script>

<style>
body {
  font-family: Arial, Helvetica, sans-serif;
  background-color: blanchedalmond;
}

button:hover {
  background-color: green;
  cursor: pointer;
}

#customerinformation {
  background-color: black;
  color: white;
}

.customerinformation {
  border: 10px double white;
}

section {
  margin: 3%;
  padding: 3%;
  border: 2px solid black;
  border-radius: 25px;
}

header {
  color: coral;
  text-align: center;
  padding: 3%;
  opacity: 0.8;
}

button {
  margin-top: 3%;
}

#header-container {
  height: 300px;
  overflow: hidden;
}

#headerpic {
  width: 100%;
  height: auto
}

h1 {
  position: absolute;
  top: 30%;
  left: 0;
  right: 0;
  transform: translateY(-50%);
  text-transform: uppercase;
  text-shadow: 5px 5px 4px #000;
  font-size: 35pt;
}

.wrapper {
  display: grid;
  grid-gap: 10px;
  grid-template-columns: repeat(3, 1fr)
}

#map {
  background: url("../../public/img/polacks.jpg");
  background-size: cover;
  width: 1920px;
  height: 1078px;
  color: black;
  cursor: grab;
}

#map-container {
  overflow: scroll;
  height: 40vh;
  width: 100%
}

nav {
  text-align: left;
  font-size: 20pt;
  font-family: 'Times New Roman', Times, serif;
  font-style: oblique;
  margin: 3%;
  border: 2px solid black;
  border-radius: 25px;

}

ul.horizontal-menu li {
  display: inline-block;
  /* margin-right: 1px; Adjust the spacing between menu items */
  /* border: 2px dotted black; */
  padding: 2%;
}

ul.horizontal-menu a {
  text-decoration: none;
  color: black;
  padding: 10px 15px;
  border: 1px solid coral;
  border-radius: 5px;
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

#receipt {
  background-color: white;
  display: inline-block;
  color: black;
  text-align: left;
  font-family: 'Times New Roman', Times, serif;
  border: 3px solid salmon;
  border-radius: 0;
}

footer {
  color: blue;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}

@media screen and (max-width: 600px) {
  .burger {
    display: inline-block;
  }
}

@media screen and (max-width: 600px) {
  ul.horizontal-menu li {
    display: flex;
  }
}
</style>