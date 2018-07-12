<template>
  <section>
    <el-table v-loading="loading" :data="items" style="width: 100%">
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
        width="150">
      </el-table-column>
      <el-table-column
        prop="fields.Description"
        label="Description"
        width="150">
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
        label="Stories"
        width="140">
      </el-table-column>
      <el-table-column
        prop="id"
        label="Actions">
        <template slot-scope="scope">
          <el-button type="text" @click="deleteRow(scope.$index, items, scope.row.id)">Delete</el-button>
        </template>
      </el-table-column>
    </el-table>
  </section>
</template>

<script>
  import Vue from 'vue'
  import Component from 'nuxt-class-component'
  import axios from 'axios'

  @Component
  export default class Epics extends Vue {
    items = []
    loading = false

    mounted () {
      this.loadItems()
    }

    loadItems () {
      this.loading = true
      axios.get('https://api.airtable.com/v0/appNQ5GNluxZKls51/Epics?api_key=keymJwFHjpkwy7E3C')
        .then(response => { this.loading = false; this.items = response.data.records })
        .catch(error => console.log(error))
    }

    deleteRow (index, rows, id) {
      const h = this.$createElement
        this.$msgbox({
          title: 'Wait a sec 😕',
          message: h('p', null, [
            h('span', null, 'Are you sure you want to delete this row?'),
          ]),
          showCancelButton: true,
          confirmButtonText: 'Absolutely',
          cancelButtonText: 'Let me think again',
          beforeClose: (action, instance, done) => {
            if (action === 'confirm') {
              instance.confirmButtonLoading = true
              instance.confirmButtonText = 'Loading...'
              
              axios.delete(`https://api.airtable.com/v0/appNQ5GNluxZKls51/Epics/${id}`, {
                headers: {
                  'Authorization': 'Bearer keymJwFHjpkwy7E3C'
                }
              }).then(response => {
                  instance.confirmButtonLoading = false
                  rows.splice(index, 1)
                  done()
                })
            } else {
              done()
            }
          }
        }).then(action => {
          this.$message({
            type: 'success',
            message: 'Row deleted successfully 🤘'
          })
        })
    }
  }
</script>
