<template>
  <div id="MultiTransition" class="container">
    <div class="row">
      <div class="col-xs-12 col-md-8 offset-md-2">
        <h1 class="pt-5 display-4">{{ title }}</h1>
        <button class="btn btn-primary my-2" @click="toggle">{{ buttonTitle }}</button>
        <div>
          <Transition name="fade" mode="out-in" appear>
            <div class="alert alert-info" v-if="show" key="info">this is some info</div>
            <div class="alert alert-warning" v-else key="warning">this is some warning</div>
          </Transition>

          <div class="jumbotron">
            <ol class="text-justify">
              <li><span class="text-primary">mode</span> mode is an attribute on transition tag where it will make delay in either leave(out) or enter(in) animation/transition.</li>
              <li>
                mode has two value
                <ul>
                  <li><span class="text-primary">out-in</span> here child will 1st leave then child will be appear</li>
                  <li><span class="text-primary">in-out</span> here child will 1st enter and then leave</li>
                </ul>
                <span class="text-danger">Note: </span><span class="small">It works if there is an element or tag which it is going to reply with other.</span>
              </li>
            </ol>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MultiTransition",
  data() {
    return {
      title: "Multi Transition",
      buttonTitle: "show",
      show: false
    };
  },
  methods: {
    toggle() {
      this.show = !this.show;
      this.buttonTitle = this.show === true ? "hide" : "show";
    }
  }
};
</script>

