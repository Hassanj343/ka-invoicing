<template>
  <app-layout title="Customers">
    <template #header>
      <h2 class="font-semibold text-xl text-gray-800 leading-tight">
        Customers - Create
      </h2>
    </template>

    <div class="py-12">
      <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
        <form class="bg-white w-1/3 mx-auto p-5 rounded-lg" @submit.prevent="onSubmit">

        <jet-validation-errors class="mb-4" />

          <FormInput name="name" label="Name" v-model="form.name" />

          <FormInput
            name="address1"
            label="Address Line 1"
            v-model="form.address1"
          />

          <FormInput
            name="address2"
            label="Address Line 2"
            v-model="form.address2"
          />

          <FormInput name="city" label="City" v-model="form.city" />

          <FormInput name="postcode" label="Postcode" v-model="form.postcode" />

          <div class="flex">
            <JetButton :isLoading="isLoading" class="mx-auto" type="submit">Submit</JetButton>
          </div>
        </form>
      </div>
    </div>
  </app-layout>
</template>

<script>
import { defineComponent, ref } from "vue";
import { useForm } from "@inertiajs/inertia-vue3";
import FormInput from "@/Components/Form/Input.vue";
import AppLayout from "@/Layouts/AppLayout.vue";
import JetButton from "@/Jetstream/Button.vue";
import JetValidationErrors from "@/Jetstream/ValidationErrors.vue";

export default defineComponent({
  components: {
    AppLayout,
    FormInput,
    JetButton,
    JetValidationErrors,
  },
  setup() {
    const form = useForm({
      name: "",
      address1: "",
      address2: "",
      city: "",
      postcode: "",
    });

    const isLoading = ref(false);

    const onSubmit = async () => {
        isLoading.value = true;
        await form.post('/customer')
        isLoading.value = false;
    };

    return {
      form,
      onSubmit,
      isLoading,
    };
  },
});
</script>

