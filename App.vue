<template>
  <view class="container">
    <text class="text-color-primary">Find Senatorial District</text>
        <text-input
        :style="{height: 40, borderColor: 'gray', borderWidth: 1}"
        v-model="text"
      />
    <button
        :on-press="senatorialDistrict(text.toLowerCase())"
        title="Find"
        color="#841584"
        accessibility-label="Find my Senatorial District"
    />
    <text class="text-color-primary">{{message}}</text>
    </view>
</template>
 
<style>
.container {
  flex: 1;
  background-color: white;
  align-items: center;
  justify-content: center;
}
.text-color-primary {
  color: blue;
  font-size: 30;
}
</style>


<script>
import senDis from '.senDis.js'
export default {
    data() {
      return {
        text: '',
        message: ''
      }
    },
    methods: {
    senatorialDistrict(userLga){
      let result = ''
      for (const sD in senDis) {
          senDis[sD].forEach(element => {
              if (userLga==element.toLowerCase()){
                  result=sD
              }
          });
      }
      this.message = result
    }
  }
}
</script>
