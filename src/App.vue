<template>
  <Tree
    v-model:nodes="data"
    row-hover-background=""
  >
    <template #label="{ label }">
      <span v-if="label === 'Animal'">🐶</span>
      <span v-if="label === 'People'">👤</span>
      {{ label }}
    </template>
    <template #afterLine="{ id, node }">
      <div style="margin-left: 10px;">
        <button>edit id: {{ id }}  {{ node.level }}</button>
      </div>
    </template>
  </Tree>
</template>

<script>
import { ref } from 'vue';
import Tree from './lib/index';

export default {
  components: {
    Tree,
  },
  setup() {
    const data = ref([
      {
        id: 1,
        label: 'Animal',
        nodes: [
          {
            id: 2,
            label: 'Dog',
          },
          {
            id: 3,
            label: 'Cat',
            nodes: [
              {
                id: 4,
                label: 'Egyptian Mau Cat',
              },
              {
                id: 5,
                label: 'Japanese Bobtail Cat',
              },
            ],
          },
        ],
      },
      {
        id: 6,
        label: 'People',
      },
    ]);

    return {
      data,
    };
  },
};
</script>
