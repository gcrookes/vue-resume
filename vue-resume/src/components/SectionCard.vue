<template>
  <div class="row justify-center text-primary q-my-sm">
    <q-card class="q-pa-sm full-width shadow-5">
      <div v-if="title" class="relative-position bg-grey-3 rounded-div" style="border-radius: 3px">
        <div class="bg-primary bar absolute"></div>
        <span class="text-h5 q-ml-md">{{ title }}</span>
      </div>
      <slot />
    </q-card>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'SectionCard',
  props: {
    title: {type: String, default: '' }
  }
})
</script>

<style lang="sass" scoped>
.bar
  width: 5px
  height: 100%
  border-radius: 3px 0px 0px 3px
</style>