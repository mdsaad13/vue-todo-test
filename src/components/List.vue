<template>
  <div>
    <div class="list" v-if="proptodo.length">
      <div class="item" v-for="(item, index) in proptodo" :key="index">
        <h3 class="mb-1">{{ item.title }}</h3>
        <p class="mb-0">{{ item.description }}</p>
        <div class="buttons mt-3">
          <button
            class="btn btn-sm btn-primary mr-2"
            @click.prevent="$root.$emit('EditItem', item)"
          >
            Edit
          </button>
          <button
            class="btn btn-sm btn-danger"
            @click.prevent="$root.$emit('DeleteItem', index)"
          >
            Delete
          </button>
        </div>
      </div>
    </div>
    <div v-else>
      <h2 class="text-center">No data found!</h2>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    proptodo: {
      type: Array,
      required: true,
    },
  },
};
</script>
<style scoped>
.list {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 20px;
}
.item {
  border-radius: 10px;
  border: 2px solid #ececec;
  padding: 20px;
}
</style>