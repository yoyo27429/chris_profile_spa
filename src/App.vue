<script>
import { ref } from "@vue/reactivity";
import { onMounted } from "@vue/runtime-core";
import AboutMe from "./components/About/AboutMe.vue";
import Education from "./components/About/Education.vue";
import Post from "./components/Project/Post.vue";
import Under from "./components/Project/Under.vue";

import AOS from "aos";
import "aos/dist/aos.css";

export default {
  name: "App",
  setup() {
    const shutterArr = [
      "shutter1",
      "shutter2",
      "shutter3",
      "shutter4",
      "shutter5",
      "shutter6",
      "shutter7",
      "shutter8",
    ];
    const start = ref(true);
    onMounted(() => {
      AOS.init();
      setTimeout(() => {
        start.value = !start.value;
      }, 100);
    });
    return { shutterArr, start };
  },
  components: {
    AboutMe,
    Education,
    Post,
    Under,
  },
};
</script>
<template>
  <!-- <transition name="startT">
    <div v-if="start" class="ret"></div>
  </transition>
  <transition name="startB">
    <div v-if="start" class="reb"></div>
  </transition> -->
  <img class="viewWindow" alt="" src="@/assets/bgc.png" />
  <div class="container">
    <AboutMe />
  </div>
  <div class="container">
    <Education />
  </div>
  <div class="container">
    <Post />
  </div>
  <div class="container">
    <Under />
  </div>
</template>

<style lang="scss">
* {
  padding: 0px;
  margin: 0px;
}
body {
  color: #e0e1dd;
  background-color: #0d1b2a;
}

.ret {
  width: 100%;
  height: 50%;
  top: 0;
  background-color: #000;
  z-index: 99999;
  position: fixed;
}
.reb {
  width: 100%;
  height: 50%;
  bottom: 0;
  background-color: #000;
  position: fixed;
  z-index: 99999;
}
.startT-enter-active,
.startT-leave-active {
  transition: all 1s ease-out;
}
.startB-enter-active,
.startB-leave-active {
  transition: all 1s ease-out;
}
.startT-leave-to {
  transform: translateY(-100%);
}
.startB-leave-to {
  transform: translateY(100%);
}
.viewWindow {
  // width: 90%;
  // margin-left: 5%;
  height: 100%;
  width: 100%;
  position: fixed;
  top: 0;
  left: 0;
  z-index: 99;
}
.container {
  margin-top: 5%;
  margin-bottom: 5%;
  height: 90%;
  width: 100%;
  float: left;
}
</style>
