<template>
  <!-- 底部导航 -->
  <footer id="tabNav">
    <section
      v-for="(item, index) of NavList"
      :key="index"
      :class="{ active: activeNavIndex === index }"
      @click="clickTab(index, item.name)"
    >
      <!--后期实时修改badge-->
      <van-icon v-if="item.name === 'Cart'" :name="item.icon" :badge="goodsNumber"/>
      <van-icon v-if="item.name !== 'Cart'" :name="item.icon" />
      <div>{{ item.title }}</div>
    </section>
  </footer>
</template>

<script>
export default {
  name: "FooterNav",
  props: {
    activeNavIndex: { type: Number, default: 0 }
  },
  data() {
    return {
      NavList: [
        { title: "首页", name: "Home", icon: "wap-home" },
        { title: "分类", name: "Category", icon: "wap-nav" },
        { title: "排行榜", name: "Rank", icon: "medal" },
        { title: "购物车", name: "Cart", icon: "shopping-cart" },
        { title: "我的", name: "User", icon: "manager" }
      ],
      goodsNumber: 0
    };
  },
  methods: {
    clickTab(index, name) {
      if (this.activeNavIndex === index) return;
      this.$router.push({ name });
    }
  }
};
</script>

<style lang="scss" scoped>
$color: #F79709;

#tabNav {
  position: fixed;
  left: 0;
  right: 0;
  bottom: 0;
  height: 13.5vw;
  display: flex;
  background: #fff;
  z-index: 100;
  section {
    flex: 1;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
    color: #7d7e80;
  }
  .active {
    color: $color;
  }
}
</style>
