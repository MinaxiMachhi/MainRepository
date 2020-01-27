<template>
  <div>
    <!-- <axiosDeo></axiosDemo> -->
    <posts></posts>
    <!-- <watcher></watcher> -->
    <!-- <method></method> -->
  </div>
</template>

<script>
import axiosDemo from "@/components/axios-demo.vue";
import propsDemo from "@/components/props-demo.vue";
import propsDemoChild from "@/components/props-demo-child.vue";
import watcher from "@/components/watcher.vue";
import method from "@/components/method.vue";
import posts from "@/components/posts";
export default {
  components: {
    propsDemo: propsDemo,
    axiosDemo: axiosDemo,
    propsDemoChild: propsDemoChild,
    watcher: watcher,
    method: method,
    posts
  }
};
</script>