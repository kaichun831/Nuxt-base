<template>
  <div>
    <transition name="home">
      <p>{{ title }}</p>
    </transition>
    <p @click="changeP">{{ pathID }}</p>
  </div>
</template>

<script>
export default {
  created() {
    // console.log(this.$route.params);
    this.pathID = this.$route.params["id"];
  },
  data() {
    return {
      title: "Title",
      pathID: "",
    };
  },
  methods: {
    changeP() {
      this.title = "NEW";
    },
  },
};
</script>

<style lang="scss" >
.home-enter-active,
.home-leave-active {
  transition: opacity 0.5s;
}
.home-enter,
.home-leave-active {
  opacity: 0;
}
</style>