<script setup lang="ts">
import { Todo, Meta } from 'components/models';
import ExampleComponent from 'components/ExampleComponent.vue';
import { ref, onServerPrefetch } from 'vue';

const selectVal = ref<string>('');
const inputVal = ref<string>('');

onServerPrefetch(() => {
  console.log('[IndexPage] on server');
});

const todos = ref<Todo[]>([
  {
    id: 1,
    content: 'ct1',
  },
  {
    id: 2,
    content: 'ct2',
  },
  {
    id: 3,
    content: 'ct3',
  },
  {
    id: 4,
    content: 'ct4',
  },
  {
    id: 5,
    content: 'ct5',
  },
]);
const meta = ref<Meta>({
  totalCount: 1200,
});
</script>

<template>
  <q-page class="row items-center justify-evenly">
    <q-btn></q-btn>
    <q-input v-model="inputVal"></q-input>
    <q-select v-model="selectVal"></q-select>
    <example-component
      title="Example component"
      active
      :todos="todos"
      :meta="meta"
    ></example-component>
  </q-page>
</template>
