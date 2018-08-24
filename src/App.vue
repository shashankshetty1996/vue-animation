<template>
  <div class="mb-5 pb-5" id="app">
    <SingleTransition />
    <hr>
    <MultiTransition name="MultiTransition" />
    <hr>
    <JSTransition />
    <hr>
    <DynamicComponent />
    <hr>
    <ListGroup />
  </div>
</template>

<script>
import SingleTransition from "./components/SingleTransition";
import MultiTransition from "./components/MultiTransition";
import JSTransition from "./components/JSTransition";
import DynamicComponent from "./components/DynamicComponent";
import ListGroup from "./components/ListGroup";

export default {
  name: "App",
  components: {
    SingleTransition,
    JSTransition,
    MultiTransition,
    DynamicComponent,
    ListGroup
  }
};
</script>

<style>
</style>
