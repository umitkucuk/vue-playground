<template>
  <section v-if="isLoading">
    <Loading />
  </section>
  <section v-else>
    <el-table :data="items" style="width: 100%">
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
        prop="fields.Target Release Date"
        label="Target Release Date"
        width="170">
      </el-table-column>
      <el-table-column
        prop="fields.Stories"
        label="Stories"
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

  import Loading from '@/components/Loading'

  @Component({
    components: { Loading }
  })
  export default class Sprints extends Vue {
    items = []
    isLoading = true
    
    mounted () {
      this.loadItems()
      this.isLoading = false
    }

    loadItems () {
      axios.get('https://api.airtable.com/v0/appNQ5GNluxZKls51/Sprints?api_key=keymJwFHjpkwy7E3C')
        .then(response => this.items = response.data.records)
        .catch(error => console.log(error))
    }
  }
</script>
