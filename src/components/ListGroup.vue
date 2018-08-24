<template>
  <div class="container">
    <div class="row">
      <div class="col-xs-12 col-md-8 offset-md-2">
        <h1 class="pt-5 display-4">{{ title }} - <span class="small font-weight-light">{{ subTitle }}</span></h1>
        <button class="btn btn-primary my-2" @click="addItem()">Add random number randomly</button>
        <ul class="list-group">
          <transition-group name="slide">
            <li
              class="list-group-item"
              v-for="(number, index) in numbers"
              :key="number"
              @click="removeItem(index)">{{ number }}</li>
          </transition-group>
        </ul>

        <div class="alert alert-primary my-2">Click on item to delete it</div>

        <div class="jumbotron text-justify">
          <p>just like transition tag, when we add name it add a new css propery else <span class="text-info" title="slide is the name added to transition-group element">slide-move</span>. Here under the hood animation is performed on transform, so we can alter it according to our use.</p>
          <p><span class="text-danger">Note: </span><span class="small">One important difference: <span class="text-info" title="<transition></transition>">transition </span>is not rendered to the DOM, But <span class="text-info" title="<transition-group></transition-group>">transition-group </span> does render a new HTML Tag!. By Default, that will be a span tag, you can overwrite this by adding <span class="text-info" title="<transition-group tag='TAG'">tag attribute</span> for transition-group</span></p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ListGroup",
  data() {
    return {
      title: "List Group",
      subTitle: "Transition Group",
      numbers: [1, 2, 3, 4, 5]
    };
  },
  methods: {
    addItem() {
      const pos = Math.floor(Math.random() * this.numbers.length);
      this.numbers.splice(pos, 0, this.numbers.length + 1);
    },
    removeItem(index) {
      this.numbers.splice(index, 1);
    }
  }
};
</script>

<style scoped>
.list-group-item {
  cursor: pointer;
}

.slide-leave-active {
  position: absolute;
}

.slide-move {
  transition: transform 1s;
}
</style>

