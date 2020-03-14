<template>
  <div>
    <cmtbox :id="$route.params.id"></cmtbox>
  </div>
</template>

<script>
import cmtbox from "../subContainer/comment.vue";

export default {
  components: {
    cmtbox
  }
};
</script>

<style lang="scss" scoped>

</style>
