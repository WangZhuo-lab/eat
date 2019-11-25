<template>
  <div>
     <i-card v-for="item in list" :key="item" i-class="split" :extra="item.name" :thumb="item.image">
         <view slot="content">{{item.remark}}</view>
         <view slot="footer">{{item.address}}</view>
     </i-card>
  </div>
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
      list:[]
    }
  },
  onLoad(option){
    this.list = require('@/data/' + option.type + '.json')
    console.log(this.list)
  },
  methods: {
  },

  created () {
  }
}
</script>

<style scoped>

</style>

