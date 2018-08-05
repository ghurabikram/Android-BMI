<template>
    <nb-container>
    <nb-header />
      <nb-content>
        <nb-form>
          <nb-item>
            <nb-input placeholder="Enter Your Name" v-model="userName"/>
          </nb-item>
          <nb-item>
            <nb-text v-if="userName">Hello, {{userName}}</nb-text>
          </nb-item>
          <nb-item>
            <nb-input v-model="weight" placeholder="Enter Your Weight in lb"/>
          </nb-item>
          <nb-item>
            <nb-input v-model="heightFtIn" placeholder="Enter Your Height in ft"/>
          </nb-item>
          
        </nb-form>
        <nb-button transparent info :onPress="calcBmi">
            <nb-text>Calculate BMI</nb-text>
        </nb-button>
        <nb-button transparent info :onPress="clearInput">
            <nb-text>Clear</nb-text>
        </nb-button>
        <nb-text v-if="bmi">BMI, {{bmi}}</nb-text>
      </nb-content>
    </nb-container>
    
</template>

<script>
import { VueNativeBase } from "native-base";
import Vue from "vue-native-core";

Vue.use(VueNativeBase);

export default {
  
  mounted: {
    
  },

  data: {
    userName: '',
    weightKg: null,
    heightFtIn: null,
    bmi: null
  },

  methods: {
    calcBmi() {
      if(this.weight && this.heightFtIn) {
        this.bmi = (this.weight * 4.88)/(this.heightFtIn*this.heightFtIn);
      }
    },
    
    clearInput() {
      this.weight = null;
      this.userName = '';
      this.heightFtIn = null;
      this.bmi = null;
    }
  
  }
};
</script>

<style>

</style>
