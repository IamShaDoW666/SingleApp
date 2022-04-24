<template>
  <Head title="{ post.title }" />
  <BreezeAuthenticatedLayout>
    <template #header>
      <h2 class="font-semibold text-xl text-gray-800 leading-tight">
        {{ post.title }}
      </h2>
    </template>
    <div class="max-w-7xl mx-auto sm:px-6 lg:px-8 mt-4">
      <div class="flex flex-col gap-y-4">
        <div class="shadow rounded bg-white p-2 text-center">
          <h1 class="text-xl sm:text-2xl font-bold">{{ post.title }}</h1>
        </div>
        <div class="shadow rounded bg-white px-6 py-4">
          <h1 class="text-sm sm:text-md">{{ post.content }}</h1>
        </div>
      </div>
    </div>
  </BreezeAuthenticatedLayout>
</template>

<script>
import BreezeAuthenticatedLayout from '@/Layouts/Authenticated.vue';
import Swal from 'sweetalert2'
import { Head, Link } from '@inertiajs/inertia-vue3';
import { Inertia } from '@inertiajs/inertia';
export default {
  components: {
    BreezeAuthenticatedLayout
  },

  props: {
    post: Object
  }

}
</script>
