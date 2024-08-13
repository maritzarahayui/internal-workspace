<template>
   <div class="flex flex-col items-center justify-center min-h-screen">
    <img alt="Vue logo" src="/assets/logo.png" class="mb-4">
    <auth />
  </div>
</template>

<script>

import Auth from "@/components/Auth.vue";

export default {
  name: "App",
  components: {
    Auth,
  },
};
</script>