<template>
  <div calss="course-list">
    <div class="list">
      <h2>添加课程</h2>
      <div>
        课程名称：
        <input type="text" v-model="name" />
      </div>
      <div>
        课程价格：
        <input type="text" v-model="price" />
      </div>
      <div>
        <button @click="handleSubmit">添加课程到列表</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CourseList",
  data() {
    return {
      name: "",
      price: ""
    };
  },
  mounted() {},
  methods: {
    handleSubmit() {
      let { name, price } = this;
      this.$parent.$emit("handleAddCourse", { name, price });
      this.name = "";
      this.price = "";
    }
  }
};
</script>
