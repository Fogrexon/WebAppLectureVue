<template>
  <div>
    <t-o-d-o-list/>
  </div>
</template>

<script>
import TODOList from "./TODOList.vue";

export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  components: {
    TODOList
  }
};
</script>

<style></style>