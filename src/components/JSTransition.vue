<template>
  <div class="container">
    <div class="row">
      <div class="col-xs-12 col-md-8 offset-md-2">
        <h1 class="mt-5 display-4">{{ title }}</h1>
        <button class="btn btn-primary my-2" @click="load = !load">Load / Remove Element</button>
        <transition
          @before-enter="beforeEnter"
          @enter="enter"
          @after-enter="afterEnter"
          @enter-cancelled="enterCancelled"

          @before-leave="beforeLeave"
          @leave="leave"
          @after-leave="afterLeave"
          @leave-cancelled="leaveCancelled"
          :css="false"
          >
          <div id="box" v-if="load"></div>
        </transition>

        <div class="jumbotron">
          <ol class="text-justify">
            <li><span class="text-primary">:css</span> is used to say vue that skip checking for css property. Go for JS.</li>
            <li><span class="text-primary">@enter and @leave</span> both of this function will receive <span class="text-info" title="enter(el, done) { done(); } and leave(el, done) { done(); }">done</span> function as it's second attribute along with el(element itself). After performing opertation we need to call <span class="text-info" title="If not called js code won't work.">done()</span></li>
          </ol>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "JSTransition",
  data() {
    return {
      title: "JavaScript Transition",
      load: false,
      elementWidth: 100
    };
  },
  methods: {
    toggle() {
      this.show = !this.show;
    },
    beforeEnter(el) {
      console.log("beforeEnter");
      this.elementWidth = 100;
      el.style.width = this.elementWidth + "px";
    },
    enter(el, done) {
      console.log("enter");
      let round = 1;
      const interval = setInterval(() => {
        el.style.width = this.elementWidth + round * 10 + "px";
        round++;
        if (round > 20) {
          clearInterval(interval);
          // done() is to make sure that program has completed
          done();
        }
      }, 20);
    },
    afterEnter(el) {
      console.log("afterEnter");
    },
    enterCancelled(el) {
      console.log("enterCancelled");
    },
    beforeLeave(el) {
      console.log("beforeLeave");
      this.elementWidth = 300;
      el.style.width = this.elementWidth + "px";
    },
    leave(el, done) {
      console.log("leave");
      let round = 1;
      const interval = setInterval(() => {
        el.style.width = this.elementWidth - round * 10 + "px";
        round++;
        if (round > 20) {
          clearInterval(interval);
          // done() is to make sure that program has completed
          done();
        }
      }, 20);
    },
    afterLeave(el) {
      console.log("afterleave");
    },
    leaveCancelled(el) {
      console.log("leaveCancelled");
    }
  }
};
</script>

<style scoped>
#box {
  width: 300px;
  height: 100px;
  background-color: #1faced;
}
</style>
