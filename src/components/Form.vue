<template>
  <div>
    <form
      action="#"
      method="post"
      class="form sticky-top"
      @submit.prevent="formSubmit"
    >
      <h3 class="text-center">{{ isInEditMode ? "Edit" : "Add" }} todo</h3>
      <div class="form-group">
        <label for="title" class="text-capitalize">title</label>
        <input
          name="title"
          type="text"
          id="title"
          class="form-control"
          v-model="form.title"
        />
      </div>
      <div class="form-group">
        <label for="description" class="text-capitalize">description</label>
        <textarea
          name="description"
          id="description"
          rows="3"
          class="form-control"
          v-model="form.description"
        ></textarea>
      </div>
      <button
        type="submit"
        class="btn btn-primary btn-block"
        :disabled="!form.title || !form.description"
      >
        Submit
      </button>
    </form>
  </div>
</template>
<script>
export default {
  data: () => ({
    form: {
      title: null,
      description: null,
    },
    isInEditMode: false,
  }),
  mounted() {
    // todo deleted
    this.$root.$on("EditItem", (item) => {
      this.isInEditMode = true;
      this.form = item;
    });
  },
  methods: {
    formSubmit() {
      if (this.isInEditMode) {
        this.$root.$emit("FormEditSubmit");
      } else {
        this.$root.$emit("FormSubmit", this.form);
      }
      this.isInEditMode = false;
      this.form = {
        title: null,
        description: null,
      };
    },
  },
};
</script>
<style scoped>
.form {
  border-radius: 10px;
  border: 2px solid #ececec;
  padding: 20px;
  top: 60px;
}
</style>