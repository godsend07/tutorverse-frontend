<script setup>
import { ref, computed } from 'vue';

const view = ref('lessons');     
const search = ref('');
const sortKey = ref('topic');
const sortDir = ref('asc');


const cart = ref([]);
const cartCount = computed(() => cart.value.reduce((s, i) => s + (i.qty || 0), 0));

function toggleCart() {
  if (view.value === 'lessons') {
    if (cart.value.length === 0) return;
    view.value = 'cart';
  } else {
    view.value = 'lessons';
  }
}


const lessons = ref([
  { id: 1, topic: 'Guitar Basics',      location: 'Hendon',       price: 55, spaces: 5, icon: 'fa-guitar' },
  { id: 2, topic: 'French Language',    location: 'Colindale',    price: 60, spaces: 5, icon: 'fa-language' },
  { id: 3, topic: 'Creative Writing',   location: 'Brent Cross',  price: 50, spaces: 5, icon: 'fa-pen-nib' },
  { id: 4, topic: 'Basketball Coaching',location: 'Golders Green',price: 45, spaces: 5, icon: 'fa-basketball-ball' },
  { id: 5, topic: 'Robotics Club',      location: 'Camden',       price: 75, spaces: 5, icon: 'fa-robot' },
  { id: 6, topic: 'Painting Workshop',  location: 'Kilburn',      price: 40, spaces: 5, icon: 'fa-paint-brush' },
  { id: 7, topic: 'Cooking Class',      location: 'Wembley',      price: 65, spaces: 5, icon: 'fa-utensils' },
  { id: 8, topic: 'Photography 101',    location: 'Euston',       price: 70, spaces: 5, icon: 'fa-camera' },
  { id: 9, topic: 'Drama & Acting',     location: 'Barnet',       price: 50, spaces: 5, icon: 'fa-theater-masks' },
  { id:10, topic: 'Football Skills',    location: 'Edgware',      price: 45, spaces: 5, icon: 'fa-futbol' }
]);


function addToCart(lesson) {
  if (lesson.spaces <= 0) return;
  const found = cart.value.find(item => item.id === lesson.id);
  if (found) found.qty += 1;
  else cart.value.push({ ...lesson, qty: 1 });
  lesson.spaces -= 1;
}

function removeFromCart(item) {
  const index = cart.value.findIndex(c => c.id === item.id);
  if (index !== -1) {
    const lesson = lessons.value.find(l => l.id === item.id);
    if (lesson) lesson.spaces += cart.value[index].qty;
    cart.value.splice(index, 1);
  }
}


const name = ref('');
const phone = ref('');
const checkoutMessage = ref('');


const nameValid = computed(() => /^[A-Za-z\s]+$/.test(name.value));
const phoneValid = computed(() => /^[0-9]+$/.test(phone.value));

function checkout() {
  if (!nameValid.value || !phoneValid.value) return;

  checkoutMessage.value = `✅ Thank you, ${name.value}! Your order has been submitted successfully.`;


  cart.value = [];
  name.value = '';
  phone.value = '';


  view.value = 'cart';


  setTimeout(() => {
    checkoutMessage.value = '';
  }, 4000);
}


</script>


<template>
  <div class="container">
    
    <header class="d-flex flex-wrap align-items-center justify-content-between py-3">
      <div class="d-flex align-items-center gap-2">
        <i class="fa-solid fa-graduation-cap"></i>
        <h1 class="h4 m-0">TutorVerse</h1>
        <small class="text-muted ms-2">after-school classes</small>
      </div>

      <div class="d-flex align-items-center gap-2">
        <input
          class="form-control"
          style="max-width: 260px"
          placeholder="Search lessons…"
          v-model="search"
        />
        <select class="form-select" style="max-width: 160px" v-model="sortKey">
          <option value="topic">Subject</option>
          <option value="location">Location</option>
          <option value="price">Price</option>
          <option value="spaces">Spaces</option>
        </select>
        <select class="form-select" style="max-width: 130px" v-model="sortDir">
          <option value="asc">Asc</option>
          <option value="desc">Desc</option>
        </select>

        <button
          class="btn btn-primary position-relative"
          :disabled="cart.length === 0 && view === 'lessons'"
          @click="toggleCart"
          title="Shopping Cart"
        >
          <i class="fa fa-shopping-cart"></i>
          <span class="ms-1">Cart</span>
          <span class="position-absolute top-0 start-100 translate-middle badge rounded-pill bg-danger">
            {{ cartCount }}
          </span>
        </button>
      </div>
    </header>

    
    <main class="py-2">
      <section v-if="view === 'lessons'">
  <div class="row g-3">
    <div class="col-md-4" v-for="lesson in lessons" :key="lesson.id">
      <div class="card h-100 shadow-sm">
        <div class="card-body">
          <h5 class="card-title text-primary">
            <i class="fa-solid" :class="lesson.icon"></i>
            {{ lesson.topic }}
          </h5>
          <p class="card-text mb-1"><strong>Location:</strong> {{ lesson.location }}</p>
          <p class="card-text mb-1"><strong>Price:</strong> £{{ lesson.price }}</p>
          <p class="card-text"><strong>Spaces:</strong> {{ lesson.spaces }}</p>
        </div>
        <div class="card-footer bg-white">
          <button class="btn btn-success w-100" :disabled="lesson.spaces <= 0" @click="addToCart(lesson)">
  Add to Cart
</button>

        </div>
      </div>
    </div>
  </div>
</section>


 <section v-else>
  <h2 class="h5 mb-3">Shopping Cart</h2>

  //Empty cart message
  <p class="text-muted" v-if="cart.length === 0">Your cart is empty.</p>

  <!-- Cart items -->
  <div v-else class="table-responsive">
    <table class="table align-middle">
      <thead>
        <tr>
          <th>Lesson</th>
          <th>Location</th>
          <th>Price</th>
          <th>Quantity</th>
          <th>Total</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in cart" :key="item.id">
          <td>
            <i class="fa-solid" :class="item.icon"></i>
            {{ item.topic }}
          </td>
          <td>{{ item.location }}</td>
          <td>£{{ item.price }}</td>
          <td>{{ item.qty }}</td>
          <td>£{{ item.price * item.qty }}</td>
          <td>
            <button class="btn btn-danger btn-sm" @click="removeFromCart(item)">
              Remove
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>

  <p class="fw-bold text-end mt-3">
    Total Price: £{{ cart.reduce((sum, i) => sum + i.price * i.qty, 0) }}
  </p>

 
<div class="mt-4 border-top pt-3">
  <h3 class="h6 mb-3">Checkout</h3>

  <div class="mb-3">
    <label class="form-label">Name</label>
    <input
      type="text"
      class="form-control"
      v-model="name"
      placeholder="Enter your name"
      :class="{ 'is-invalid': name && !nameValid }"
    />
    <div class="invalid-feedback">Name must contain letters only.</div>
  </div>

  <div class="mb-3">
    <label class="form-label">Phone</label>
    <input
      type="text"
      class="form-control"
      v-model="phone"
      placeholder="Enter your phone number"
      :class="{ 'is-invalid': phone && !phoneValid }"
    />
    <div class="invalid-feedback">Phone must contain numbers only.</div>
  </div>

  <button
    class="btn btn-primary"
    :disabled="!nameValid || !phoneValid || cart.length === 0"
    @click="checkout"
  >
    Checkout
  </button>

  <p v-if="checkoutMessage" class="alert alert-success mt-3">{{ checkoutMessage }}</p>
</div>

</section>

    </main>
  </div>
</template>
