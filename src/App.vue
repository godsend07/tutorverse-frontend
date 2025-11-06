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
    if (cart.value.length === 0) return; // disabled when empty
    view.value = 'cart';
  } else {
    view.value = 'lessons';
  }
}
</script>

<template>
  <div class="container">
    <!-- Header -->
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
        <p class="text-muted">Lessons will appear here (list, sort, search). Coming next.</p>
        
      </section>

      <section v-else>
        <h2 class="h5 mb-2">Shopping Cart</h2>
        <p class="text-muted" v-if="cart.length === 0">No items yet.</p>
     
      </section>
    </main>
  </div>
</template>
