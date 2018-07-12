<template>
  <section>
    <el-table v-loading="loading" :data="items" style="width: 100%">
      <el-table-column
        type="index"
        width="40">
      </el-table-column>
      <el-table-column
        prop="fields.Name"
        label="Name"
        width="200">
      </el-table-column>
      <el-table-column
        prop="fields.Facets"
        label="Facets"
        width="350">
      </el-table-column>
      <el-table-column
        prop="fields.Notes"
        label="Notes">
      </el-table-column>
    </el-table>
  </section>
</template>

<script>
  import Vue from 'vue'
  import Component from 'nuxt-class-component'
  import axios from 'axios'

  @Component
  export default class AppSections extends Vue {
    items = []
    loading = false
    
    mounted () {
      this.loadItems()
    }

    loadItems () {
      this.loading = true
      axios.get('https://api.airtable.com/v0/appNQ5GNluxZKls51/Sprints?api_key=keymJwFHjpkwy7E3C')
        .then(response => { this.loading = false; this.items = response.data.records })
        .catch(error => console.log(error))
    }
  }
</script>
