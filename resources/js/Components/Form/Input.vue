<template>
  <div class="my-4">
    <jet-label :for="name" :value="label" />
    <jet-input
      :id="name"
      :name="name"
      :type="type"
      class="mt-1 block w-full"
      :required="required"
      v-model="inputValue"
    />
  </div>
</template>

<script>
import JetInput from "@/Jetstream/Input.vue";
import JetLabel from "@/Jetstream/Label.vue";
import {computed} from 'vue';

export default {
  components: {
    JetLabel,
    JetInput,
  },
  props: {
      name: {
          type: String,
          default: null
      },
      type:{
          type: String,
          default: 'text'
      },
      label:{
          type: String,
          default: null
      },
      required: {
          type: Boolean,
          default: false,
      },

      modelValue: {
          type: [String, Number],
          default: null,
      }
  },

  setup(props, {emit}){
      const inputValue = computed({
          get: () => props.modelValue,
          set: (value) => emit('update:modelValue', value)
      });

      return {
          inputValue,
      }
  }
};
</script>
