<template>
  <div class="m-menu">
    <dl class="nav" @mouseleave="mouseLeave">
      <dt>全部分类</dt>
      <dd v-for="(item, index) in menu" :key="index" @mouseenter="mouseEntry">
        <i :class="item.type"></i>{{ item.name }}<span class="arrow"></span>
      </dd>
    </dl>
    <div class="detail" v-show="kind" @mouseenter="stay" @mouseleave="leave">
      <template v-for="(item, index) in curDetail.child">
        <h4>{{ item.title }}</h4>
        <span v-for="(item2, index2) in item.child">{{ item2 }}</span>
      </template>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      kind: "",
      menu: [
        {
          type: "food",
          name: "美食",
          child: [
            {
              title: "美食",
              child: ["代金券", "甜点饮品", "火锅", "自助餐", "小吃快餐"],
            },
          ],
        },
        {
          type: "takeout",
          name: "外卖",
          child: [
            {
              title: "外卖",
              child: ["美团外卖"],
            },
          ],
        },
        {
          type: "hotel",
          name: "酒店",
          child: [
            {
              title: "酒店星级",
              child: ["经济型", "舒适/三星", "高档/四星", "豪华/五星"],
            },
          ],
        },
      ],
    };
  },
  computed: {
    curDetail() {
      let x = this.menu.filter((item) => item.type === this.kind)[0];
      let y = {};
      Object.assign(y, x);
      return y;
    },
  },
  methods: {
    mouseLeave() {
      this. _time = setTimeout(() => {
        this.kind = "";
      }, 150);
    },
    mouseEntry(e) {
      this.kind = e.target.querySelector("i").className;
    },
    stay(){
      clearTimeout(this._time)
    },
    leave(){
      this.kind = ''
    }
  },
};
</script>

<style lang='scss'>
</style>