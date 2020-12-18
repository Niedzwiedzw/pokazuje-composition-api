<template>
  <div class="App">
    {{ helloMessage }}
      <button @click="updateName">Od tylu</button>
      <input placeholder="imie boże" type="text" v-model="name" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, Ref, computed } from "vue";

function useMessageLogic(text: Ref<string>) {
    const helloMessage = computed(() => {
        return `this is ${text.value}'s app do chuja`;
    });
    const updateName = () => {
        text.value = text.value.split('').reverse().join('');
    };
    return {
        helloMessage,
        updateName,
    }
}

export default defineComponent({
  name: "App",
  props: {},
  setup() {
      const name = ref("Paweł");
      // function helloMessage() {
      //     return `this is ${name.value}'s app do chuja`;
      // }
      // function updateName() {
      //     name.value = name.value.split('').reverse().join('');
      // }

      return {
          name,
          ...useMessageLogic(name),
      };
  },
});
</script>

<style scoped lang="scss">
.App {
}
</style>
