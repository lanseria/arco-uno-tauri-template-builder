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
      <div class="p-8 text-lg font-bold">
        Count is: {{ count }}
      </div>

      <div class="w-full space-x-2">
        <button type="button" class="btn" @click="count++">
          Add 1
        </button>
        <button type="button" class="btn" @click="backendAdd">
          Add 2 in backend
        </button>
      </div>
    </div>
  </div>
</template>
