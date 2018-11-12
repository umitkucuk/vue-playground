<template>
  <section>



    <h2>Salt Vue Examples</h2>
    <br>
    <hr>
    <br>
    <el-row>
      <el-col :span="4">
        <div>
          <el-input placeholder="Enter Your Name Please" v-model="input"></el-input>
        </div>
      </el-col>
    </el-row>
    <br>

    <el-button :plain="true" type="primary" round @click="greeting(input) ">
      Click Me
    </el-button>

  </section>
</template>

<script>

  import Vue from 'vue'
  import Component from 'nuxt-class-component'


  @Component
  export default class SaltPage extends Vue {

    greeting (input) {
        this.$message( "Welcome " + input + value12)
    }
  }
</script>


<style>

</style>
