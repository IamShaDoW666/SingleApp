<template>
  <Head title="About" />
  <BreezeAuthenticatedLayout>
    <template #header>
      <h2 class="font-semibold text-xl text-gray-800 leading-tight">
        About
      </h2>
    </template>
    <div class="max-w-7xl mx-auto sm:px-6 lg:px-8 mt-4">
      <div class="p-3">
        Coming Soon..
      </div>
    </div>
  </BreezeAuthenticatedLayout>
</template>
<script>
import BreezeAuthenticatedLayout from '@/Layouts/Authenticated.vue';
import { Head } from '@inertiajs/inertia-vue3';
export default {
  components: {
    BreezeAuthenticatedLayout,
    Head
  }
}
</script>
