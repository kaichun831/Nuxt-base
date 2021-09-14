<template>
  <div>
    <p>Home</p>
    <button @click="$store.commit('increment')">
      {{ $store.state.counter }}
    </button>
    <p>{{ mountains }}</p>
    <p>{{ initData }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  async asyncData() {
    // const aData = await axios.get("https://api.nuxtjs.dev/mountains");
    const aData = await axios.post(
      `${process.env.BASE_URL}WmsWebApi_Post/api/Menu/GetRfAuthMenuList`,
      {},
      {
        headers: {
          Authorization: "Bearer RF",
        },
      }
    );
    console.log(aData);
    return {
      initData: aData.data,
    };
  },
  // async fetch() {
  //   // this.mountains = await fetch("https://api.nuxtjs.dev/mountains").then(
  //   //   (res) => res.json()
  //   // );
  //   this.mountains = await fetch(
  //     `${process.env.BASE_URL}WmsWebApi_Post/api/Menu/GetRfAuthMenuList`,
  //     { method: "POST", headers: { Authorization: "Bearer RF" } }
  //   ).then((res) => res.json());
  // },
  data() {
    return {
      mountains: [],
    };
  },
  created() {
    // axios.defaults.baseURL = process.env.BASE_URL;
    // axios.defaults.headers.common["Authorization"] = "Bearer RF";
    // axios.defaults.headers.post["Content-Type"] =
    //   "application/x-www-form-urlencoded";
  },
  activated() {
    // Call fetch again if last fetch more than 30 sec ago
    if (this.$fetchState.timestamp <= Date.now() - 30000) {
      this.$fetch();
    }
  },
};
</script>
<style lang="scss" scoped>
.container {
  background: rgb(165, 165, 165);
  box-shadow: 1px 1px rgb(117, 117, 117);
  ul {
    list-style: none;
  }
}

.slide-bottom-enter-active,
.slide-bottom-leave-active {
  transition: opacity 0.25s ease-in-out, transform 0.25s ease-in-out;
}
.slide-bottom-enter,
.slide-bottom-leave-to {
  opacity: 0;
  transform: translate3d(0, 15px, 0);
}
</style>
