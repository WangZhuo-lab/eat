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
        {name:"香奈儿新春礼盒",address:"江汉区-解放大道688号-武商广场",image:"cloud://eat-ukl2e.6561-eat-ukl2e-1300844576/chanel58 57 43.jpg",remark:"内置chanel58冬天的丝绒红棕色，57秋天丝绒枫叶红，43春夏俏皮颜色珊瑚色"},
        {name:"女神隔离",address:"淘宝vicividi官方旗舰店",image:"cloud://eat-ukl2e.6561-eat-ukl2e-1300844576/nvshen.jpg",remark:"提亮+隔离+妆前乳三合一，滋润不油腻，还有SPF30+防晒！"},
        {name:"爱敬持久气垫",address:"江岸区-中山大道756号-大洋百货",image:"cloud://eat-ukl2e.6561-eat-ukl2e-1300844576/age.jpg",remark:"分为三款，适用于各肤质，平价好用性价比超高！"},
        {name:"纪梵希四宫格散粉",address:"江汉区-解放大道690号-武汉国际广场",image:"cloud://eat-ukl2e.6561-eat-ukl2e-1300844576/givenchy.jpg",remark:"细腻粉质 轻盈定妆 控油持妆"}
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
