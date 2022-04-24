<template>
  <div class="mx-auto max-w-6xl pt-4">
    <Link :href="route('posts.index')" :class="{ 'text-blue-700': $page.component === 'Posts/Index' }" class="hover:text-gray-500">Posts</Link>
    <Link :href="route('pages.about')" :class="{ 'text-blue-700': $page.component === 'About' }" class="ml-2 hover:text-gray-500">About</Link>

    <slot />

  </div>
</template>

<script>
import { Link } from '@inertiajs/inertia-vue3';
export default {
    components: {
        Link,
    }
}
</script>
