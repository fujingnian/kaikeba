<template>
  <div>
    <h1>购物车</h1>
    <hr />
    <course-list></course-list>
    <market-list :list="marketList"></market-list>
    <cart-list :list="cartList"></cart-list>
  </div>
</template>

<script>
import CourseList from "@/components/CourseList";
import MarketList from "@/components/MarketList";
import CartList from "@/components/CartList";
export default {
  name: "cart",
  components: {
    CourseList,
    MarketList,
    CartList
  },
  data() {
    return {
      marketList: [
        {
          name: "超屌的课程",
          price: 9997
        },
        {
          name: "更屌的课程",
          price: 9998
        },
        {
          name: "最屌的课程",
          price: 9999
        }
      ],
      cartList: []
    };
  },
  mounted() {
    this.handleAddCourse();
    this.handleAddCart();
    this.cartChange();
  },
  methods: {
    handleAddCourse() {
      this.$on("handleAddCourse", row => {
        this.marketList.push(row);
      });
    },
    handleAddCart() {
      this.$on("handleAddCart", row => {
        let list = this.cartList.filter(e => {
          return e.name == row.name;
        });

        console.log(list);

        if (list.length == 0) {
          this.cartList.push(Object.assign({ number: 1 }, row));
          return;
        }

        this.cartList.forEach(e => {
          if (e.name == row.name) e.number++;
        });
      });
    },
    cartChange() {
      this.$on("cartChange", (row, flag) => {
        this.cartList.forEach((e, i) => {
          if (e.name == row.name) {
            switch (flag) {
              case "-":
                e.number--;
                break;
              case "+":
                e.number++;
                break;
            }
          }
          if (e.number == 0) this.cartList.splice(i, 1);
        });
      });
    }
  }
};
</script>
