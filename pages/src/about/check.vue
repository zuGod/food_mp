<template>
  <view>
    <button class="btn btn1" @click="checkTo()">系统介绍</button>
    <button class="btn" @click="canTo()">功能介绍</button>

    <view class="title">
      {{ title }}
    </view>
    <view class="word1">
      {{ word1 }}
    </view>
    <view class="title">
      {{ title2 }}
    </view>
    <view class="word2"> {{word2}} </view>
    <view class="word2"> {{word3}} </view>
    <view class="word2"> {{word4}} </view>
    <view class="word2"> {{word5}} </view>
    <view class="word2"> {{word6}} </view>
    <view class="word2"> {{word7}} </view>

  </view>
</template>

<script>
export default {
  data() {
    return {
      title: "简介",
      word1:
        "食品安全涉及千家万户，关系到人民群众的身体健康，关系到经济健康发展和社会稳定。由于缺乏有效的手段，检测的流程没有系统化，从而导致很多问题层出不穷，例如检测资源浪费，检测资源信息分割、部门间重复抽检等现象十分突出，监管手段难以形成快速反应机制。建立统一的食品安全送检体系，做好送检流程，完善送检机制，搞好食品质量管理，提高食品突发事件快速反应能力必须依靠信息化手段。建立“食品安全检验检测信息共享平台”，有效整合各监管部门检测数据，实现相互沟通和信息共享，已成为加强食品安全监管一种有效的手段。",
      title2: "我们的建设目标",
      word2:
        "1.	整合食品安全检测资源。针对食品检测资源分散各相关职能部门的现状，按照检测任务，结合各部门监管实际情况，制定全年检测计划，有序合理规划和分配各部门检测资源、检测项目、检测样品，以达到整合资源、减少重复投资、提高检测能力、资源与结果共享的目标。",
      word3:
        "2.	建成食品安全监测信息共享平台。将食品安全监测技术与信息技术、网络通讯等先进技术相结合，通过统一制定食品安全监测数据信息交换标准，采集各地区、农委、食药品、出入境检验检疫，质监、工商、卫生等各部门的监督抽查详细检测数据，构建食品安全监测信息共享平台，及时对外发布食品安全监测信息，为消费者、企业和政府提供监测信息服务。",
      word4:
        "3.	实现食品安全动态监管。以现有食品安全风险预警系统为基础，建立科学的监测数据风险预警模型，依托食品安全监测数据共享平台，对各地区、卫生、农业、工商、质监、商业等各部门报送的食品安全监测信息包含溯源信息进行集中处理，及时发现敏感性问题、行业性问题、区域性问题，及时进行分类评估并发布预警通报，形成长效机制。",
      word5:
        "4.	全市统一食品安全预警信息共享体系。分别建立预警信息共享市级服务平台（主平台）和预警信息共享县级服务平台（子平台）。主平台与子平台相互链接，集合全市食品检测信息，实现食品安全信息全市共享，扩大安全预警范围，提高食品安全防范效果。",
      word6:
        "5.	实现统一通信支撑系统的使用。实现覆盖中国移动、电信、联通等多家通信服务商的通信支撑系统，方便各部门相关人员接收食品安全预警信息提醒和相关工作任务。",
      word7:
        "6.	实现本地化数字化资源的复合应用接口。可为后期实现市政务地图系统支撑的区域预警及分析警报，实现市清结算系统支撑的食品流通监管及送检申请等复合功能的数据接口。",
    };
  },
  methods: {
    canTo(){
        uni.navigateTo({ url: './can' })
    },
    checkTo(){
        uni.navigateTo({ url: './check' })
    }
  },
};
</script>
<style scoped>
.title {
  flex: auto;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-size: 18px;
  margin: 8px;
  font-style: inherit;
}
.word1 {
  text-indent: 30px;
  padding: 0px 20px;
  line-height: 30px;
  border-bottom: 1px solid rgb(136, 132, 132);
}
.word2{
    text-indent: 30px;
  padding: 0px 20px;
  line-height: 30px;
}
.btn {
  display: flex;
  width: 50%;
  justify-content: center;
  align-items: center;
  height: 40px;
  line-height: 40px;
}
.btn1 {
  float: left;
}
</style>