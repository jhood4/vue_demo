<template>
  <div class="card">
    <DataTable :value="products" tableStyle="min-width: 50rem">
      <Column
        v-for="col of columns"
        :key="col.field"
        :field="col.field"
        :header="col.header"
      >
        <template #body="slotProps">
          <component
            :is="col.component"
            v-bind="{ data: slotProps.data[col.field] }"
          />
        </template>
      </Column>
    </DataTable>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { ProductService } from '@/service/ProductService';
import ButtonExample from '@/ButtonExample.vue';
import BadgeExample from '@/BadgeExample.vue';

onMounted(() => {
  ProductService.getProductsMini().then((data) => (products.value = data));
});

const products = ref();
const columns = [
  { field: 'code', header: 'Code', component: ButtonExample },
  { field: 'name', header: 'Name', component: BadgeExample },
  { field: 'category', header: 'Category', component: ButtonExample },
  { field: 'quantity', header: 'Quantity', component: BadgeExample },
];
</script>
