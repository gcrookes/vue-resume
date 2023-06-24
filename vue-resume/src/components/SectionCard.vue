<template>
  <div class="row justify-center text-primary q-my-md">
    <q-card class="q-pa-sm full-width shadow-5">
      <div v-if="title" class="relative-position bg-grey-3 rounded-div row justify-between" style="border-radius: 3px">
        <div class="bg-primary bar absolute"></div>
        <div class="text-h5 q-ml-md">{{ title }}</div>
        <div v-if="icon" class="bg-accent q-mx-sm q-my-xs rounded-div icon">
          <q-icon :name="icon" size="1.5rem" color="black"/>
        </div>
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
    title: {type: String, default: '' },
    icon: {type: String, default: '' },
  }
})
</script>

<style lang="sass" scoped>
.bar
  width: 5px
  height: 100%
  border-radius: 3px 0px 0px 3px
.rounded-div
  border-radius: 5px 5px 5px 5px

.icon
  border: solid black 1px

</style>
