<script setup>
import { ref, onMounted } from 'vue'
import { supabase } from './lib/supabaseClient'

const comment = ref([])

async function getComment() {
  const { data } = await supabase.from('comment').select()
  comment.value = data
}

onMounted(() => {
  getComment()
})
</script>

<template>
<h1>Comments</h1>
  <ul>
    <li v-for="comment in comment" :key="comment.id">{{ comment.name }} {{ comment.comment }}
    </li>
  </ul>
<h2>comments</h2>
</template>
