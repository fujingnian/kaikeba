<template>
  <div calss="course-list">
    <hr />
    <h2>商品列表</h2>
    <table class="list">
      <tr>
        <th>商品名称</th>
        <th>商品价格</th>
        <th></th>
      </tr>
      <tr v-for="(e,index) in  list" :key="index">
        <td>{{ e.name }}</td>
        <td>{{ e.price }}</td>
        <td>
          <button @click="handleAddCart(e)">添加商品</button>
        </td>
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
      id: 0
    };
  },
  mounted() {},
  methods: {
    handleAddCart(row) {
      this.$parent.$emit("handleAddCart", { ...row, id: this.id++ });
    }
  }
};
</script>

<style lang="scss" scoped>
.list {
  margin: 0 auto;
}
</style>
