<template>
  <div class="container">
    <div class="row">
      <div class="col-xs-12 col-md-8 offset-md-2">
        <h1 class="mt-5 display-4">Animations</h1>
        <hr>
        <div class="d-block my-2">
          <button class="btn btn-primary mb-3 mr-2" @click="toggle()">Show Alert</button>
          <button class="btn btn-primary mb-3" @click="toggleAnimateCSS()">Animate.css</button>
          <select v-model="alertAnimation" class="form-control">
            <option value="fade">fade</option>
            <option value="slide">slide</option>
          </select>
        </div>
        <div>
          <h2 class="text-primary my-2">Transition tag Basic - transition and animation</h2>
          <transition name="fade">
            <div class="alert alert-info" v-if="show">some alert info using transition</div>
          </transition>
          <!-- <transition name="slide">
            <div class="alert alert-warning" v-if="show">some alert info using transition and animation with problem without giving type (Don't use this)</div>
          </transition> -->
          <transition name="slide" type="animation">
            <div class="alert alert-info" v-if="show">some alert info using transition and animation</div>
          </transition>
          <transition name="slide" type="animation" appear>
            <div class="alert alert-info" v-show="show">some alert info using transition and animation</div>
          </transition>
          <transition :name="alertAnimation">
            <div class="alert alert-info" v-if="show">some alert info using transition effect based on drop down</div>
          </transition>
        </div>
        <hr>
        <div>
          <h2 class="text-primary my-2">Animate.css</h2>
          <transition
            enter-active-class="animated bounce"
            leave-active-class="animated shake"
            >
            <div class="alert alert-info" v-if="animateCSS">Animate.css</div>
          </transition>
        </div>

        <div class="jumbotron">
          <ol class="text-justify">
            <li><span class="text-primary">Transition</span> It is the vue reserve element which is used to perform animation on it's child<span class="d-block"><span class="text-danger">Note: </span><span class="small">Transition applices for only one chlid component at a time</span></span></li>
            <li><span class="text-primary">name</span> It can be a dynamic attribute for Transition tag which says what css animation we are using. <span class="d-block"><span class="text-danger">Note: </span><span class="small">if we use name as <span class="text-info" title="<Transition name='fade'>...</Transition>">fade</span> then following css classes can be used.
            <ul>
              <li>fade-enter</li>
              <li>fade-enter-active</li>
              <li>fade-leave</li>
              <li>fade-leave-active</li>
            </ul></span>
            </span>
            </li>
            <li>
              <span class="text-primary">type </span>attribute can be used when you have both transition and animation on a single Transition tag. It accepts either animation or transition. Based on the value it will give more preference.
            </li>
            <li><span class="text-primary">appear </span>attribute will add effort on trigger.</li>
            <li><span class="text-primary">External Animation library</span> We can use external library such as <em>animated.css</em>, while applying class we can target <span class="text-info" title="fade is the name given for Transition tag">fade-enter-active </span>and <span class="text-info" title="fade is the name given for Transition tag">fade-leave-active </span>for adding the feactures.</li>
          </ol>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SingleTransition",
  data() {
    return {
      show: false,
      animateCSS: false,
      alertAnimation: "fade"
    };
  },
  methods: {
    toggle() {
      this.show = !this.show;
    },
    toggleAnimateCSS() {
      this.animateCSS = !this.animateCSS;
    }
  }
};
</script>

<style>
.fade-enter {
  opacity: 0;
}

.fade-enter-active {
  transition: opacity 1s;
}

.fade-leave {
  /* opacity: 1; */
}

.fade-leave-active {
  transition: opacity 1s;
  opacity: 0;
}

.slide-enter {
  opacity: 0;
  /* transform: translateY(20px); */
}

.slide-enter-active {
  animation: slide-in 0.5s ease-in-out forwards;
  transition: opacity 0.5s;
}

.slide-leave {
}

.slide-leave-active {
  animation: slide-out 0.5s ease-in-out forwards;
  transition: opacity 3s;
  opacity: 0;
}

@keyframes slide-in {
  from {
    transform: translateY(20px);
  }

  to {
    transform: translateY(0);
  }
}

@keyframes slide-out {
  from {
    transform: translateY(0);
  }

  to {
    transform: translateY(20px);
  }
}
</style>
