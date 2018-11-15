<template>
  <div style="text-align: center; align-items: center; align-content: center">
    <section>
      <br>
      <h2>Salt Vue Examples</h2>
      <br>
      <hr>
      <br>
      <h3>
        Greeting
      </h3>
      <br>
      <div>
        <el-input type="text" placeholder="Please Enter Your Name" v-model="inputName"></el-input>
      </div>
      <br>
      <el-button :disabled="inputName === ''" :plain="true" type="primary" @click="greeting(inputName)" >
        Click Me
      </el-button>
      <br><br>
      <h3>Todo list comin.</h3>
      <br>
      <hr>
      <br>

      <div>
        <el-table
          :data="arr"
          style="width: auto"
        >
          <el-table-column
            prop="arr"
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
    arr = []
    inputName = ''

    computed(){
      this.toggle()
    }

    greeting (inputName) {
      this.$message( "Welcome " + this.inputName)
      console.log(this.inputName.length)

      this.arr.push(this.inputName)
      console.log(this.arr)
    }
  }
</script>


<style>

</style>
