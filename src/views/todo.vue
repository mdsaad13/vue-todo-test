<template>
  <div class="row">
    <List :proptodo="todo" class="col-lg-8" />
    <Form class="col-lg-4" />
  </div>
</template>

<script>
import List from "@/components/List.vue";
import Form from "@/components/Form.vue";

export default {
  components: {
    List,
    Form,
  },
  data: () => ({
    todo: [],
  }),
  mounted() {
    this.restoreTodo();

    // new todo added
    this.$root.$on("FormSubmit", (newitem) => {
      this.todo.unshift(newitem);
      this.updateTodoInLocalStorage();
    });

    // todo deleted
    this.$root.$on("DeleteItem", (indexToDelete) => {
      this.todo.splice(indexToDelete, 1);
      this.updateTodoInLocalStorage();
    });

    // todo edited
    this.$root.$on("FormEditSubmit", () => {
      this.updateTodoInLocalStorage();
    });
  },
  methods: {
    restoreTodo() {
      this.todo = localStorage.getItem("todo-list")
        ? JSON.parse(localStorage.getItem("todo-list"))
        : [];
    },
    updateTodoInLocalStorage() {
      localStorage.setItem("todo-list", JSON.stringify(this.todo));
    },
  },
};
</script>
<style >
</style>