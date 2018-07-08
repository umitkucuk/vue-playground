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
        prop="fields.Epic Name"
        label="Epic Name"
        width="180">
      </el-table-column>
      <el-table-column
        prop="fields.Blocks Release"
        label="Blocks Release"
        width="170">
      </el-table-column>
      <el-table-column
        prop="fields.Epic Title"
        label="Epic Title"
        width="180">
      </el-table-column>
      <el-table-column
        prop="fields.Description"
        label="Description"
        width="180">
      </el-table-column>
      <el-table-column
        prop="fields.RobEst"
        label="RobEst"
        width="70">
      </el-table-column>
      <el-table-column
        prop="fields.Blocked by (Epic)"
        label="Blocked by (Epic)"
        width="140">
      </el-table-column>
      <el-table-column
        prop="fields.Stories"
        label="Stories">
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
  export default class Epics extends Vue {
    items = []
    isLoading = true
    
    mounted () {
      this.loadItems()
      this.isLoading = false
    }

    loadItems () {
      axios.get('https://api.airtable.com/v0/appNQ5GNluxZKls51/Epics?api_key=keymJwFHjpkwy7E3C')
        .then(response => this.items = response.data.records)
        .catch(error => console.log(error))
    }
  }
</script>
