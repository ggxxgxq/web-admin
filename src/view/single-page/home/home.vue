<template>
  <div>
    <Row :gutter="20">
      <i-col
        :xs="12"
        :md="8"
        :lg="6"
        v-for="(infor, i) in inforCardData"
        :key="`infor-${i}`"
        style="height: 120px; padding-bottom: 10px"
      >
        <infor-card
          shadow
          :color="infor.color"
          :icon="infor.icon"
          :icon-size="36"
        >
          <count-to :end="infor.count" count-class="count-style" />
          <p>{{ infor.title }}</p>
        </infor-card>
      </i-col>
    </Row>
    <Row :gutter="20" style="margin-top: 10px">
      <i-col :md="24" :lg="8" style="margin-bottom: 20px">
        <Card shadow>
          <chart-pie
            style="height: 300px"
            :value="pieData"
            text="新闻类别"
          ></chart-pie>
        </Card>
      </i-col>
      <i-col :md="24" :lg="16" style="margin-bottom: 20px">
        <Card shadow>
          <chart-bar
            style="height: 300px"
            :value="barData"
            text="每周用户活跃量"
          />
        </Card>
      </i-col>
    </Row>
    <Row>
      <Card shadow>
        <example style="height: 310px" />
      </Card>
    </Row>
  </div>
</template>

<script>
import InforCard from "_c/info-card";
import CountTo from "_c/count-to";
import { ChartPie, ChartBar } from "_c/charts";
import Example from "./example.vue";

export default {
  name: "home",
  components: {
    InforCard,
    CountTo,
    ChartPie,
    ChartBar,
    Example,
  },
  data() {
    return {
      inforCardData: [
        {
          title: "新增用户",
          icon: "md-person-add",
          count: 803,
          color: "#2d8cf0",
        },
        { title: "累计点击", icon: "md-locate", count: 232, color: "#19be6b" },
        {
          title: "点赞互动",
          icon: "md-chatbubbles",
          count: 12,
          color: "#E46CBB",
        },
        { title: "新增评论", icon: "md-map", count: 14, color: "#9A66E4" },
      ],
      pieData: [
        { value: 14, name: "财经" },
        { value: 22, name: "科技" },
        { value: 5, name: "娱乐" },
        { value: 0, name: "美食" },
        { value: 2, name: "家庭" },
      ],
      barData: {
        周一: 13,
        周二: 10,
        周三: 9,
        周四: 8,
        周五: 6,
        周五: 2,
        周六: 3,
        周日: 15,
      },
    };
  },
  mounted() {
    //
  },
};
</script>

<style lang="less">
.count-style {
  font-size: 50px;
}
</style>
