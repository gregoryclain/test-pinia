<template>
  <form class="form" @submit.prevent="submit">
    <div class="mb-3">
      <label class="form-label">Name</label>
      <input v-model="inputs.name" class="form-control" />
    </div>
    <div class="mb-3">
      <label class="form-label">Url</label>
      <input v-model="inputs.url" class="form-control" />
    </div>
    <button type="submit" class="btn btn-success">Add</button>
  </form>
</template>

<script lang="ts">
import { defineComponent, reactive } from "vue";
import { useCartStore } from "@/store/cart";

export default defineComponent({
  setup() {
    const inputs = reactive({ name: "", url: "" });
    const cart = useCartStore();
    const submit = () => {
      cart.addItem({ ...inputs });
      inputs.name = "";
      inputs.url = "";
    };
    return { inputs, submit };
  },
});
</script>
