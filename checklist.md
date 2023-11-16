# Checklist

Before you submit the final version of your labs, make sure that your project fullfills all of the tasks that will be added to this checklist.

## 00 Introduction

- [x] Install an IDE on your system

## 01 Git

- [x] Fork and clone the 1md031-lab-21 repository

## 02 HTML

Your index.html file contains:
- [x] A headline
- [x] A section to select burgers that contains at least three items. Each item has:
    - [x] A name
    - [x] An image
    - [x] Information about allergies 
- [x] A section to collect customer information:
    - [x] First- and Last Name (in one field)
    - [x] E-Mail Address
    - [x] Street
    - [x] House Number (only allowing numbers in this field)
    - [x] Gender (male, female, do not wish to provide as radio buttons)
- [x] A button to place the order
- [x] Ensure the website loads when opening http://localhost:8080/

## 03 CSS

The style.css file contains:
- [x] A rule to make the allergy information bold
- [x] Different text and background color for the two different sections (burger selection and customer information)
- [x] Change the cursor when hovering over the order button
- [x] Adds margins to the sections and the order button
- [x] Add a border to the two sections
- [x] Create a header that places an image behind the headline
- [x] Use a grid layout for the burger selection section

console.log("Aardvark" < "Zoroaster")

console.log(null || "user")

const obj = {a: 123};
console.log(obj['a'] === obj.a);
const obj = {a: 123, b: 321};
let {a} = obj;
console.log(a);


<head><body>onload=""onclick=""

<script>


index.htmlpublicindex-noscript.html
index-for-Vue-part-of-tutorial.htmlpublicindex.html
src
http://localhost:8080/index-noscript.html
http://localhost:8080/#/dispatcher
HomeView.vuesrc/viewsDispatcher.vue<template>...</template><script>...</script><style>...</style>
console.log()console.log


//Object Constructor Function

function Employee(fn, ln, branch, pos) {
    this.firstName = fn; // The *this* keyword refers to the object itself
    this.lastName = ln;
    this.branch = branch;
    this.position = pos;
    this.name = function() {
        return this.firstName + ' ' + this.lastName;
    };
}

// Objects are then instantiated using the *new* keyword
const emp = new Employee('Maike', 'Paetzel', 'Uppsala', 'PhD Student');

console.log( emp.firstName ); // Output: Maike
console.log( emp.name() ); // Output: Maike Paetzel

const emp = { firstName: 'Maike', 
               lastName: 'Paetzel', 
                 branch: 'Uppsala', 
                    pos: 'PhD Student',
                   name: function () {
                           return this.firstName + ' ' + this.lastName;
                         }
            }

console.log( emp.firstName ); // Output: Maike
console.log( emp.name() ); // Output: Maike Paetzel









//Getting Nodes

// To get an element with a specific ID, use getElementById()
const el = document.getElementById('anID');

// To get a NodeList of all elements of a specific class, use getElementsByClassName()
const els = document.getElementsByClassName('aClassName');

// To get a NodeList of all elements with a specific name, use getElementsByName()
const els = document.getElementsByName('aName');

// To get a NodeList of all elements of a certain type, use getElementsByTagName()
const els = document.getElementsByTagName('p'); 
// Returns all paragraph elements in the document
el.previousSiblingel.nextSiblingel.childNodesel.parentNode


<!-- Manipulate HTML with JavaScript (HTML) -->
<div id="myID">
</div>
//Manipulate HTML with JavaScript (JS)
document.getElementById("myID").innerHTML = "Välj en burgare";

//Creating or Changing Nodes

// Use the createElement() method to create any HTML element
const btn = document.createElement('button');

// Use the createTextNode() method to create text content
const txt = document.createTextNode('Click Here');

// Use the appendChild() method of a node object to add one node inside another
btn.appendChild(txt);

// We can set an attribute to the element node using the setAttribute() method
btn.setAttribute('class', 'aButtonClass');

// We can also read attributes using the getAttribute() mehtod
console.log( btn.getAttribute('class') ); // Output: aButtonClass

// In order to display this newly created element, we have to append it to an existing
// node in the document. In this case we add it directly to the body.
document.body.appendChild(btn);

<!-- Manipulate HTML with Vue (HTML) -->
<div>
    {{ yourVariable }}
</div>
data

//Manipulate HTML in Vue SFC (JS)
  data: function () {
    return {
      yourVariable: 'Välj en burgare'
    }
  }


<!-- Dynamic text -->
<input type="text" v-model="yourVariable">
<div>
  {{ yourVariable }}
</div>
HomeView.vueyourVariabledatayourVariable


v-modelv-bindv-on

<!-- Dynamic text -->
<input type="text" v-bind:value="yourVariable" v-on:input="yourVariable = $event.target.value">
<div>
  {{ yourVariable }}
</div>

HomeView.vuenamecomponentmethodsdatadataburgerstemplateburgers

<Burger v-for="burger in burgers"
            v-bind:burger="burger" 
            v-bind:key="burger.name"/>
burgersburgerkeyv-bind

<script>import Burger from '../components/OneBurger.vue'OneBurger.vueOneBurger.vueHomeView.vuetemplatescriptstyletemplatescriptexport defaultnamepropspropsburgerspropsburger<Burger />burgerv-bind:burger="yourObject"


scriptHomeView.vueexport default
letvarconst
Array(3) [ {…}, {…}, {…} ]
0: Object { name: "Barger", kCal: 300, url: "pic", lactose: false, gluten: true }
1: Object { name: "Birger", kCal: 400, url: "pic", lactose: true, gluten: true }
2: Object { name: "Berger", kCal: 500, url: "pic", lactose: false, gluten: false }
burgers: yourArrayReferencelocalhost:8080
styledocument.getElementById('aParagraphID').style.color = 'green';stylebackground-colorbackgroundColorcolorbackground

style=""var col = document.getElementById('aParagraphID').style.color;style=""getComputedStyle()windowwindow.getComputedStyle(element, pseudo-element);null


//Adding and Removing Class Attributes
const myElement = document.getElementById("myID");
myElement.classList.remove("originalClass");
myElement.classList.add("newClass");

<div v-bind:class="['alwaysUsedClass', { redClass: shouldBeRed }]">
  Text
</div>
booleanExpression

display

<!-- Conditional Statements using JS (HTML, version 1) -->
<div id="myID" style="display:none">
    <p>This text is conditionally visible</p>
</div>
//Conditional Statements using JS (JS, version 1)

const myElement = document.getElementById("myID");
myElement.style.display = booleanExpression ? '' : 'none';

<!-- Conditional Statements using JS (HTML, version 2) -->
<div id="myID">
</div>
//Conditional Statements using JS (JS, version 2)
const myElement = document.getElementById("myID");
if (booleanExpression && !myElement.hasChildNodes()) {
    myElement.innerHTML = "<p>This text is conditionally visible</p>";
}
else if (!booleanExpression) {
    myElement.innerHTML =  ""
}

<!-- Conditional Statements using Vue -->
<div id="myID">
    <p v-if="booleanExpression">This text is conditionally visible</p>
</div>
booleanExpressionbooleanExpression: true


// Loops in JavaScript

for (let i; i < 5; i++) {
    // Do something five times
}

// for-in loop
for (let i in array) {
    // Do something for all elements in the array
    // array[i] references the object
}

// for-of loop
for (let x of array) {
    // Do something for all elements in the array
    // x references the object
}

<!-- Loops in Vue -->
<li v-for="x in object"> </li>
<!-- NOTE that x references the object, NOT the index, here -->
burgers

<!-- Loop Example with condition in Vue -->
<li v-for="burger in burgers" v-bind:key="burger.name">
  {{ burger.name }} 
  <span v-if="burger.kCal > 400">
    BIG MEAL
  </span>
</li>

<!-- Loop Example in JavaScript (HTML) -->
<ol id="myid">
</ol>
//Loop Example in JavaScript (JS)

const myElement = document.getElementById("myid");
const warningText = document.createTextNode(" BIG MEAL");
for (let burger of b) {
    let listItem = document.createElement("li");
    let listValue = document.createTextNode(burger.name);
    listItem.appendChild(listValue);
    if (burger.kCal > 400)
    {
        let warning = document.createElement("span");
        warning.appendChild(warningText);
        listItem.appendChild(warning);
    }
    myElement.appendChild(listItem);
}

bodyindex-noscript.htmltemplateHomeView.vue
style.cssstyleHomeView.vue

OneBurger.vue
OneBurger.vue{{ burger.name }}v-bind:src="burger.img"
HomeView.vue<Burger>



assetssrc
menu.json
//Menu JSON
[
  {
    "name": "Ostburgare",
    "kCal": 850,
    "lactose": true,
    "gluten": false,
    "img": "url/to/your/img"
  }
]
import menu from '../assets/menu.json'menu

//Triggering Functions Through Events
var myButton = document.getElementbyId('myButtonID');

// In JavaScript you can either trigger an event directly on an object
myButton.onclick = functionName;

// Or using the event handler function
myButton.addEventListener("click", functionName);

// You can pass a defined function as above (no parentheses), 
// or provide an anonymous function
myButton.onclick = function () {
    ...
}
methods

<!-- Vue v-on:click (HTML) -->
<div id="orders">
    <button v-on:click="markDone(key)">Klart</button>
</div>
//Vue v-on:click (JS)
methods: {
  markDone: function() {
    //Add some functionality
  }
}

name=v-model=
v-on:click=thisthis.variableName
v-bind:attributeprops: { attribute: type }




OneBurger.vue
data: function () {
  return {
    amountOrdered: 0,
  }
},
{{ amountOrdered }}

this.$emit('eventName', payload)eventNamev-on:eventName="someFunction($event)"$eventsomeFunctionpayload

// In child component
addBurger: function () {
  this.amountOrdered += 1;
  this.$emit('orderedBurger', { name:   this.burger.name, 
                                amount: this.amountOrdered 
                              }
  );
},
<!-- template in parent component -->
<Burger v-for="burger in burgers"
        v-bind:burger="burger" 
        v-bind:key="burger.name"
        v-on:orderedBurger="addToOrder($event)"/>
// script in parent component
addToOrder: function (event) {
  this.orderedBurgers[event.name] = event.amount;
},
orderedBurgers



HomeView.vuelocalhost:8080/#/dispatcher

<!-- Sending messages (HTML) -->

<div id="map" v-on:click="addOrder">
  click here
</div>
<div>

HomeView.vue

//Sending messages (Vue)
addOrder: function (event) {
  var offset = {x: event.currentTarget.getBoundingClientRect().left,
                y: event.currentTarget.getBoundingClientRect().top};
  socket.emit("addOrder", { orderId: this.getOrderNumber(),
                            details: { x: event.clientX - 10 - offset.x,
                                       y: event.clientY - 10 - offset.y },
                            orderItems: ["Beans", "Curry"]
                          }
             );
},
addOrdersocket.emit()server.jssocket.on()addOrderorder

// When a connected client emits an "addOrder" message
socket.on('addOrder', function (order) {
  data.addOrder(order);
  // send updated info to all connected clients, note the use of io instead of socket
  io.emit('currentQueue', { orders: data.getAllOrders() });
});


{ orders:
  { 77900: { orderId: 77900,
             details: { x: 479,
                        y: 156 
                      },
             orderItems: [ "Beans", "Curry"]
           },
    17432: { orderId: 17432,
             details: { x: 134,
                        y: 273 
                      },
             orderItems: [ "Beans", "Curry"]
           }
  }
}
orders


{ 77900: { details: { x: 479,
                      y: 156 
                    },
           orderItems: [ "Beans", "Curry"]
         },
  17432: { details: { x: 134,
                      y: 273 
                    },
           orderItems: [ "Beans", "Curry"]
         }
}
orderItemsDispatcher.vue

//Receiving messages (Vue)
export default {
  name: 'Dispatcher',
  data: function () {
    return {
      orders: null
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
created: function () {...}socket.on()socket.on('currentQueue', ... )this.ordersdata.ordersthisthis.ordersorders

Dispatcher.vue

<div id="dots">
  <div v-for="(order, key) in orders" 
       v-bind:style="{ left: order.details.x + 'px', 
                       top: order.details.y + 'px'}" 
       v-bind:key="'dots' + key">
    {{ key }}
  </div>
</div>
divv-fororderdiv{{ key }}v-bind:key="'dots' + key"v-binddetails

//Displaying messages (HTML)
<div v-bind:style="{ left: order.details.x + 'px', 
                      top: order.details.y + 'px' }">
    T
</div>


background: url("/img/polacks.jpg");
overflow: scroll
localhost:8080/#/dispatcherDispatcher.vue
location: { x: 0,
            y: 0
          }
ordersv-bind:style="{}"Dispatcher.vue


socket.emit

//Dispatcher View (HTML)

<div id="orderList">
  <div v-for="(order, key) in orders">
    #{{ key }}: {{ order.orderItems.join(", ") }}
  </div>
</div>
v-for


HomeView.vue
orders{{orders}}
HomeView.vueDispatcher.vue
node_modules


checklist.md

## 04 JavaScript and Vue

- [x] You have a menu.json file which contains at least three different burgers with respective attributes

Your HomeView.vue file:
- [x] ... contains a MenuItem constructor (that is not used)
- [x] ... loads the information from the menu.json object and inserts the information to the burger selection section
- [x] ... allows the customer to click in the interactive map to select delivery location
- [x] ... has an order button that sends the information from the text boxes, the gender, all items on the order, and the delivery location to the server (to be realyed to the dispatcher)

Your OneBurger.vue component:
- [x] ... allows adding and removing burgers from the order
- [x] ... only displays allergy information if relevant (either only if it contains gluten or lactose, or only if it's gluten or lactose free)

Your Dispatcher.vue file:
- [x] ... shows for every order :
    - [x] a location on the map
    - [x] the order information
    - [x] the customer information

## Optional
- [x] Only allow the order to be sent if all necessary information are provided
- [x] Display receipt on the customer page as well
- [ ] Allow the dispatcher to handle orders by providing buttons next to every order that can switch the order status to "in preparation" and "done"
- [ ] Display the order status to the customer and update it in the customer view if updated by the dispatcher
- [ ] Show the order status for the customer as well.
- [ ] Find a better visualization for what orders belong to which location on the map