<template>
  <div calss="course-list">
    <hr />
    <h2>购物车</h2>
    <table class="list">
      <tr>
        <th>商品名称</th>
        <th>商品价格</th>
        <th>商品数量</th>
        <th>合计</th>
      </tr>
      <tr v-for="(e,index) in  list" :key="index">
        <td>{{ e.name }}</td>
        <td>{{ e.price }}</td>
        <td>
          <button @click="cartChange(e,'-')">-</button>
          {{ e.number }}
          <button @click="cartChange(e,'+')">+</button>
        </td>
        <td>{{ e.price*e.number }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "CourseList",
  props: ["list"],
  data() {
    return {
      name: "",
      price: ""
    };
  },
  mounted() {},
  methods: {
    cartChange() {
      this.$parent.$emit("cartChange", arguments[0], arguments[1]);
    }
  }
};
</script>

<style lang="scss" scoped>
.list {
  margin: 0 auto;
}
</style>