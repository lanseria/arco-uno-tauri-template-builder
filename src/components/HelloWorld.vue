<script setup lang="ts">
import { invoke } from '@tauri-apps/api/tauri'

defineProps<{ msg: string }>()

const count = ref(0)
async function backendAdd() {
  count.value = await invoke('backend_add', { number: count.value })
}
</script>

<template>
  <div class="mx-auto w-9/12">
    <div class="my-6 justify-center border border-white/10 text-center">
      <h1 class="text-blue-5 font-bold">
        {{ msg }}
      </h1>
      <div class="p-4 text-lg font-bold">
        Count is: {{ count }}
      </div>

      <div class="w-full space-x-2">
        <AButton type="primary" @click="count++">
          Add 1
        </AButton>
        <AButton type="primary" @click="backendAdd">
          Add 2 in backend
        </AButton>
      </div>
    </div>
  </div>
</template>
