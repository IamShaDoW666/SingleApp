<template>
  <Head title="Create" />
  <BreezeAuthenticatedLayout>
    <template #header>
      <h2 class="font-semibold text-xl text-gray-800 leading-tight">
        Create
      </h2>
    </template>
    <div class="max-w-7xl mx-auto sm:px-6 lg:px-8 mt-4">
      <form @submit.prevent="submit">
        <div>
          <BreezeLabel for="title" value="Title" />
          <BreezeInput id="title" type="text" class="mt-1 block w-full" v-model="form.title" autofocus/>
          <div class="text-red-600 bg-red-100 rounded p-2 m-2" v-if="form.errors.title">{{ form.errors.title }}</div>
        </div>

        <div class="mt-4">
          <BreezeLabel for="content" value="Content" />
          <BreezeInput id="content" type="text" class="mt-1 block w-full" v-model="form.content"/>
          <div class="text-red-600 bg-red-100 rounded p-2 m-2" v-if="form.errors.content">
            {{ form.errors.content }}
          </div>
        </div>

        <div class="flex items-center justify-end mt-4">
          <BreezeButton class="ml-4" :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
            Create
          </BreezeButton>
        </div>
      </form>
    </div>
  </BreezeAuthenticatedLayout>
</template>

<script>
import BreezeAuthenticatedLayout from '@/Layouts/Authenticated.vue';
import BreezeButton from '@/Components/Button.vue';
import BreezeCheckbox from '@/Components/Checkbox.vue';
import BreezeGuestLayout from '@/Layouts/Guest.vue';
import BreezeInput from '@/Components/Input.vue';
import BreezeLabel from '@/Components/Label.vue';
import Swal from 'sweetalert2';

import { Head, Link, useForm } from '@inertiajs/inertia-vue3';
export default {
  components: {
    BreezeAuthenticatedLayout,
    BreezeButton,
    BreezeCheckbox,
    BreezeCheckbox,
    BreezeGuestLayout,
    BreezeInput,
    BreezeLabel,
    Link,
    useForm,
    Head

  },

  setup() {
    const form = useForm({
      title: '',
      content: '',

    })

    const submit = () => {
      form.post(route('posts.store'), {
        onSuccess: () => {
          Swal.fire({
            icon: "success",
            title: "Post Created Successfully!"
          })
        }
      });
    }

    return { form, submit }
  }
}

</script>
