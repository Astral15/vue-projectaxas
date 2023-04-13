<template>
  <div>
    <p v-if="errorMessage">{{ errorMessage }}</p>
    <ul v-else>
      <li v-for="user in users" :key="user.id">{{ user }}</li>
    </ul>
  </div>
  <div class="grid grid-cols-3 gap-3">
    <div>01</div>
    <div>09</div>
  </div>
</template>

<script setup>
import axios from 'axios';
import { ref } from 'vue';

const useFetchUsers = async (url) => {
  const users = ref([]);
  const errorMessage = ref(null);

  try {
    const response = await axios.get(url);
    users.value = response.data;
  } catch (error) {
    errorMessage.value = error.message;
    console.error(error);
  }

  return { users, errorMessage };
};

</script>
