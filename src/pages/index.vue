<template>
</template>

<script lang="ts" setup>
import { onBeforeMount } from 'vue';
import { useRoute } from 'vue-router';
import { useStorage } from '@vueuse/core'
import { TokenApi } from 'spacegt';

const route = useRoute()

const token = useStorage<any>('token', undefined)

onBeforeMount(async () => {
  if (route.query.token) {
    if (route.query.token == 'remove') {
      token.value = undefined
    } else
      token.value = route.query.token
    return;
  }

  if (token.value) {
    const res = await TokenApi.validate(token.value)

    if (!res) {
      token.value = undefined
      return;
    };

    const messageData = {
      type: 'token',
      payload: token.value
    };
    window.parent.postMessage(messageData, '*');
  }
})
</script>
