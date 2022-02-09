<template>
    <ul>
        <resource-item v-for="res in resources" :key="res.id" :resObj="res"></resource-item>
    </ul>
</template>

<script>
import ResourceItem from './ResourceItem.vue';

    export default {
        name: 'StoredResource',
        inject: ['resources'],
        components: {
            'resource-item': ResourceItem,
        },
    }
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>