<template>
  <q-page>
    <p v-for="post in posts" :key="post.id">
      {{ post.title }}
    </p>
  </q-page>
</template>

<style></style>

<script setup>
import { ref, onMounted } from "vue";
import { api } from "../boot/axios";

defineOptions({
  name: "IndexPage",
});

const posts = ref([]);

onMounted(async () => {
  const { data } = await api.get("/posts");
  posts.value = data;
});
</script>
