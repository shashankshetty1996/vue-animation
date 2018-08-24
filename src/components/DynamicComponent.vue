<template>
  <div class="container">
    <div class="row">
      <div class="col-xs-12 col-md-8 offset-md-2">
        <h1 class="pt-5 display-4">{{ title }}</h1>
        <button class="btn btn-primary my-2" @click="toggleComponents()">Toggle components</button>
        <Transition name="fade" mode="out-in">
          <component :is="selectedComponent"></component>
        </Transition>

        <div class="jumbotron text-justify">
          <p>We can also use <span class="text-info" title="Special tag is special tag in vue.js. Which render other vue components, based on component name which is passed on to the :is attribute">component tag </span>. To add transition to this componet tag, we can wrap this with Transition Tag.</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import DangerAlert from "./DangerAlert";
import SuccessAlert from "./SuccessAlert";

export default {
  name: "DynamicComponent",
  data() {
    return {
      title: "Dynamic Components",
      selectedComponent: "app-success-alert"
    };
  },
  methods: {
    toggleComponents() {
      this.selectedComponent =
        this.selectedComponent == "app-success-alert"
          ? "app-danger-alert"
          : "app-success-alert";
    }
  },
  components: {
    appDangerAlert: DangerAlert,
    appSuccessAlert: SuccessAlert
  }
};
</script>

