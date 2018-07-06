<template>
  <section>
    <h2>Hey! I found your IP address: <el-tag>{{ ip }}</el-tag> 😎</h2>
  </section>
</template>

<script>
  import axios from 'axios'

  export default {
    asyncData({ req, params }) {
      return axios.get('https://api.ipify.org?format=json')
        .then((res) => {
          return { ip: res.data.ip }
        })
    }
  }
</script>
