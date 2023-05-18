<template>
  <!-- <router-view /> -->
  <q-card color="q-pa-md cf-shadow-1 q-ma-xl">
    <div class="flex items-center q-mx-md q-gutter-x-md">
      <div class="q-py-xs">
        <div class="text-12 text-weight-medium">
          Movie Theater Ticket Website
        </div>
        <div class="text-10">
          <q-list class="q-ma-xs q-pa-xs">
            <q-item class="q-ma-xs q-pa-xs" icon="circle">Created a website where users can find and purchase tickets for a movie theater</q-item>
            <q-item class="q-ma-xs q-pa-xs" icon="check_circle">Frontend implemented using React, users can login or use the site as a guest</q-item>
            <q-item class="q-ma-xs q-pa-xs" icon="check_circle">Backend implemented in Spring Boot, with data stored on a MySQL database</q-item>
          </q-list>
        </div>
      </div>
    </div>
  </q-card>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'App',
});
</script>
