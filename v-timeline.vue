<template src="./template.html"></template>
<style src="./style.css" scoped></style>

<script>
import genericPoints from "./points.js"

export default {
  name: "v-timeline",
  props: {
    pointers: genericPoints,
  },
  data() {
    return {
      points: this.pointers,
      pointActive: 1,
    };
  },
  watch: {
    pointers(value) {
      this.points = value;
    }
  },
  methods: {
    clickHandler(obj) {
      this.move(obj.axis);
      this.pointActive = obj.id;
    },
    move(axis) {
      window.scroll({
        top: axis.y || 0,
        left: axis.x || 0,
        behavior: "smooth"
      });
    }
  }
};
</script>
