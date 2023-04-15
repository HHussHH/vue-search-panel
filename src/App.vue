<script setup>
import { ref, computed } from "vue";

const products = ref([
  { title: "Бананы", price: 200 },
  { title: "Яблоки", price: 300 },
  { title: "Апельсины", price: 100 },
  { title: "Кола", price: 250 },
  { title: "Торт", price: 120 },
  { title: "Сыр", price: 420 },
  { title: "Колбаса", price: 2300 },
  { title: "Шоколад", price: 400 },
]);

const query = ref("");

const queryProducts = computed(() => {
  let p = products.value;
  let search = query.value;
  if (search) {
    p = p.filter((product) => {
      return product.title.indexOf(search) !== -1 || product.price <= search;
    });
  }
  return p;
});
</script>

<template>
  <div>
    <input type="search" placeholder="Поиск продуктов..." v-model="query" />
    <br /><br />

    {{ query }}
    <ul>
      <li v-for="product in queryProducts" :key="product">
        {{ product.title }} -
        <sap>{{ product.price.toLocaleString() }} ₽</sap>
      </li>
    </ul>
  </div>
</template>
