<template>
  <div>
    <div v-if="proptodo.length">
      <transition-group name="fade" mode="out-in" tag="div" class="list">
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
      </transition-group>
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
<style lang="scss" scoped>
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

// zoom-grow
.zoom-grow-enter-active,
.zoom-grow-leave-active {
  animation-duration: 0.25s;
  animation-fill-mode: both;
  animation-name: zoom-out;
  transform-style: preserve-3d;
}

.zoom-grow-leave-active {
  animation-direction: reverse;
  transform-style: preserve-3d;
}

.zoom-grow-enter-to {
  animation-duration: 0.25s;
  animation-fill-mode: both;
  animation-name: zoom-out;
  transform-style: preserve-3d;
}

@keyframes zoom {
  from {
    opacity: 0;
    transform: scale3d(1.2, 1.2, 1.2);
  }

  100% {
    opacity: 1;
  }
}

@keyframes zoom-out {
  from {
    opacity: 0;
    transform: scale3d(0.2, 0.2, 0.2);
  }

  100% {
    opacity: 1;
  }
}
</style>