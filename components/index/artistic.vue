<template>
  <section class="m-istyle">
    <dl @mouseover="over">
      <dt>有格调</dt>
      <dd :class="{ active: kind === 'all' }" kind="all" keyword="景点">
        全部
      </dd>
      <dd :class="{ active: kind === 'part' }" kind="part" keyword="美食">
        约会聚餐
      </dd>
      <dd :class="{ active: kind === 'spa' }" kind="spa" keyword="丽人">
        丽人SPA
      </dd>
      <dd :class="{ active: kind === 'movie' }" kind="movie" keyword="电影">
        电影演出
      </dd>
      <dd :class="{ active: kind === 'travel' }" kind="travel" keyword="旅游">
        品质出游
      </dd>
    </dl>
    <ul class="ibody">
      <li v-for="item in curList" :key="item.title">
        <el-card :body-style="{ padding: '0px' }" shadow="never">
          <img :src="item.img" class="image" />
          <ul class="cbody">
            <li class="title">{{ item.title }}</li>
            <li class="pos">
              <span>{{ item.pos }}</span>
            </li>
            <li class="price">
              ￥<em>{{ item.price }}</em
              ><span>/起</span>
            </li>
          </ul>
        </el-card>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  data() {
    return {
      kind: "all",
      list:{
        all: [{
          type:'all',
          title:'quanbu',
          img:''
        }],
        part: [{
          type:'all',
          title:'quanbu',
          img:''
        }],
        spa: [{
          type:'all',
          title:'quanbu',
          img:''
        }],
        movie: [{
          type:'all',
          title:'quanbu',
          img:''
        }],
        travel: [{
          type:'all',
          title:'quanbu',
          img:''
        }]
      }
    };
  },
  computed: {
    curList() {
      return this.list[this.kind]
    },
  },
  methods: {
    over(e) {
      let dom = e.target
      let tag = dom.tagName.toLowerCase()
      if(tag === 'dd'){
        this.kind = dom.getAttribute('kind')
      }
    },
  },
};
</script>

<style lang='scss'>
@import "@/assets/css/index/artistic.scss";
</style>
