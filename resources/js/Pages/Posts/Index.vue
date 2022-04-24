<template>
  <Head title="Posts" />
  <BreezeAuthenticatedLayout>
    <template #header>
      <h2 class="font-semibold text-xl text-gray-800 leading-tight">
        Posts
      </h2>
    </template>
    <div class="max-w-7xl mx-auto sm:px-6 lg:px-8 mt-4">
      <Link :href="route('posts.create')" class="float-right px-4 mb-3 py-2 mr-2 rounded bg-indigo-400 hover:bg-indigo-300 font-bold">
        Create Post
      </Link>
      <table class="min-w-full shadow-md rounded">
        <thead class="bg-gray-300 rounded">
          <tr>
            <th class="p-4 text-left font-bold">ID</th>
            <th class="p-4 text-left font-bold">Title</th>
            <th class="p-4 text-left font-bold">Content</th>
            <th class="p-4 text-left font-bold">Created at</th>
            <th class="p-4 text-left font-bold">Actions</th>
          </tr>
        </thead>
        <tbody class="divide-y divide-gray-300 bg-white">
          <tr v-for="post in posts" :key="post.id" class="hover:bg-gray-100 cursor-pointer">
            <td class="p-4">{{ post.id }}</td>
            <td class="p-4">{{ post.title }}</td>
            <td class="p-4">{{ post.content }}</td>
            <td class="p-4">{{ post.created_at }}</td>
            <td class="p-4">
              <!-- <Link :href="route('posts.edit')" name="editButton" class="px-4 mb-3 lg:mb-0 py-2 mr-2 rounded bg-indigo-400 hover:bg-indigo-300 font-bold">
                Edit
              </Link> -->
              <Button @click="deletePost(post.id)" method="POST" name="deleteButton" class="px-4 py-2 rounded bg-red-400 hover:bg-red-300 font-bold">
                Delete
            </Button>
            </td>
          </tr>
        </tbody>
      </table>
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
    BreezeAuthenticatedLayout,
    Link,
    Head

  },

  props: {
    posts: Object
  },

  setup() {
    const deletePost = (id) => {
      Swal.fire({
        title: 'Are You Sure? ',
        showDenyButton: true,
        showCancelButton: true,
        confirmButtonText: 'Yes',
        denyButtonText: 'No',
        customClass: {
          actions: 'my-actions',
          cancelButton: 'order-1 right-gap',
          confirmButton: 'order-2',
          denyButton: 'order-3',
        }
      }).then((result) => {
        if (result.isConfirmed) {
          Inertia.delete(route('posts.destroy', id))
        } else if (result.isDenied) {
          Swal.fire('Changes are not saved', '', 'info')
        }
      })

    }

    return {
      deletePost,

    }

  }

}

</script>
