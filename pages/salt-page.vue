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
        <el-input v-bind:id="inputx" type="text" placeholder="Please Enter Your Name" v-model="inputx"></el-input>
      </div>
      <br>
      <keep-alive>
        <el-button :plain="true" type="primary" v-bind:disabled=!isDisable  v-on:click="greeting(inputx)" >
          Click Me
        </el-button>
      </keep-alive>
      <el-button :plain="true" type="primary"   v-on:click="toggle()" >
        Toggle
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
    arr = [];
    inputx = "";
    isDisable = false;


    computed(){
      this.toggle()
    }


    toggle(){

      if(this.inputx.length > 0){
        this.isDisable=true
      }else {
        this.isDisable=false
      }
      console.log(this.isDisable)
    }


    greeting (inputx) {
      this.$message( "Welcome " + this.inputx);
      console.log(this.inputx.length);

      this.arr.push(this.inputx);
      console.log(this.arr);
    }
  }
</script>


<style>

</style>
