<template>
  <div class="pr-40 min-h-full shadow">
    <nav class="fixed w-40 pt-6">
      <ul>
        <li v-for="page in pages" :key="page.slug">
          <DocsSidenavItem class="px-6" :page="page" />
        </li>
      </ul>
    </nav>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import { Page } from '@/plugins/docs'

export default Vue.extend({
  name: 'DocsSidenav',
  data: () => ({ pages: [] as Page[] }),
  async fetch() {
    this.pages = await this.$docs.fetch()
  },
})
</script>
