<template>
  <button
    :type="type"
    class="
      inline-flex
      items-center
      px-4
      py-2
      bg-gray-800
      border border-transparent
      rounded-md
      font-semibold
      text-xs text-white
      uppercase
      tracking-widest
      hover:bg-gray-700
      active:bg-gray-900
      focus:outline-none
      focus:border-gray-900
      focus:ring focus:ring-gray-300
      disabled:opacity-25
      transition
    "
    :class="btnClasses"
  >
    <slot></slot>
  </button>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  props: {
    isLoading: Boolean,
    type: {
      type: String,
      default: "submit",
    },
  },

  setup(props) {
    const btnClasses = {
      "disabled opacity-75": !!props.isLoading,
    };

    return {
      btnClasses,
    };
  },
});
</script>
