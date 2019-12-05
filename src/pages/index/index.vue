<template>
  <div>
   <swiper
      :indicator-dots="indicatorDots"
      :autoplay="autoplay"
      :interval="interval"
      :duration="duration"
      style="height:200px"
    >
    <block v-for="img in imgUrls" :key="img">
      <swiper-item>
        <image :src="img" style="width:100%;"/>
      </swiper-item>
    </block>
  </swiper>
  <i-grid i-class="no-border">
    <i-grid-item @click="goType(grid)" v-for="grid in grids" :key="grid" i-class="no-border">
        <i-grid-icon>
            <image :src="grid.image" />
        </i-grid-icon>
        <i-grid-label>{{grid.title}}</i-grid-label>
    </i-grid-item>
  </i-grid>
   <i-panel :title="title_name">
    <view style="padding: 15px;">
     <i-card v-for="item in top" :key="item" i-class="split" :extra="item.name" :thumb="item.image">
         <view slot="content">{{item.remark}}</view>
         <view slot="footer">{{item.address}}</view>
     </i-card>
    </view>
  </i-panel>
  </div>
</template>

<script>

export default {
  data () {
    return {
      title_name:"hot",
      grids:[
        {title:"口红",image:"/static/images/kouhong.png"},
        {title:"粉底",image:"/static/images/fendi.png"},
        {title:"眼影",image:"/static/images/yanying.png"},
        {title:"眉笔",image:"/static/images/meibi.png"}
      ],
      top:[
        {name:"香奈儿新春礼盒",address:"地址1",image:"cloud://eat-ukl2e.6561-eat-ukl2e-1300844576/chanel58 57 43.jpg",remark:"内置chanel 58 57 43三款口红"},
        {name:"女神隔离",address:"地址2",image:"cloud://eat-ukl2e.6561-eat-ukl2e-1300844576/nvshen.jpg",remark:"介绍2"},
        {name:"爱敬持久气垫",address:"地址3",image:"cloud://eat-ukl2e.6561-eat-ukl2e-1300844576/age.jpg",remark:"介绍3"},
        {name:"纪梵希四宫格散粉",address:"地址4",image:"cloud://eat-ukl2e.6561-eat-ukl2e-1300844576/givenchy.jpg",remark:"介绍4"}
      ],
      imgUrls: [
        'cloud://eat-ukl2e.6561-eat-ukl2e-1300844576/huadong5.jpg',
        'cloud://eat-ukl2e.6561-eat-ukl2e-1300844576/huadong4.jpg',
        'cloud://eat-ukl2e.6561-eat-ukl2e-1300844576/huadong3.jpg',
        'cloud://eat-ukl2e.6561-eat-ukl2e-1300844576/huadong2.jpg',
        'cloud://eat-ukl2e.6561-eat-ukl2e-1300844576/huadong1.jpg'
      ],
      indicatorDots: false,
      autoplay: false,
      interval: 5000,
      duration: 1000,
    }
  },

  methods: {
    goType(type){
      console.log(type)
      let url ='../list/main?type=' + type.title
      mpvue.navigateTo({ url })
    }
  },

  created () {
  }
}
</script>

<style scoped>
div >>>.no-border{
  border-width:0pt;
}
div >>>.split{
  margin-bottom:10pt;
}
</style>
