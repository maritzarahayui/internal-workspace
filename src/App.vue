<template>
   <div class="flex flex-col items-center justify-center min-h-screen">
    <br>
    <img alt="Vue logo" src="https://seeklogo.com/images/V/vuejs-logo-17D586B587-seeklogo.com.png" class="mb-4">
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