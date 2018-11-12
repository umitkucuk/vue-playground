<template>
  <div style="text-align: center; align-items: center; align-content: center">
  <section>
    <br>
    <h2>Salt Vue Examples</h2>
    <br>
    <hr>
    <br>
        <div>
          <el-input placeholder="Please Enter Your Name" v-model="input"></el-input>
        </div>
        <br>
        <el-button :plain="true" type="primary" round @click="greeting(input) ">
          Click Me
        </el-button>

        <div>
          <el-table
            :data="arr"
            style="width: auto"
          >
            <el-table-column
              prop=""
              label="Inputs"
            >
            </el-table-column>
          </el-table>

        </div>


  </section>
  </div>
</template>

<script>
  import Vue from 'vue'
  import Component from 'nuxt-class-component'


  @Component
  export default class SaltPage extends Vue {
    data() {
      return {
        value2: 3
      }
    }
    arr = [];
    greeting (input) {
        this.$message( "Welcome " + input);
        console.log(this.arr + input);
        this.arr.push(input);
        console.log(this.arr)

    }


  }
</script>


<style>

</style>
