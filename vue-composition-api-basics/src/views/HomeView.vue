<template>
  <div class="home">
    <div>
      <h2>{{ apptitle }}</h2>

      <h3>{{ counterData.title }}:</h3>
      <div @click="sub(2)" class="btn">--</div>
      <div @click="sub(1)" class="btn">-</div>
      <span class="counter">{{ counterData.count }}</span>
      <div @click="add(1)" class="btn">+</div>
      <div @click="add(2)" class="btn">++</div>
    </div>

    <p>This counter is {{ oddOrEven }}</p>

    <div class="edit">
      <h4>Edit Counter Title:</h4>
      <input v-model="counterData.title" type="text" />
    </div>
  </div>
</template>

<script setup>
/* Imports*/
import {
  reactive,
  computed,
  watch,
  // onBeforeUpdate,
  // onUpdated,
  onMounted,
  // onBeforeUnmount,
  // onBeforeMount,
  // onUnmounted,
  // onActivated,
  // onDeactivated,
} from "vue";

/* 
App Titile  */
const apptitle = "My Amazing Counter App";

onMounted(() => {
  console.log("Do stuff related to App title");
});

// const counter = ref(0),
//   counterTitle = ref("My Counter");

/**  
 Counter 
*/

const counterData = reactive({
  count: 10,
  title: "My Counter",
});

watch(
  () => counterData.count,
  (newCount) => {
    if (newCount === 20) {
      alert("Way to go! You made it to 20");
    }
    // console.log("new Count", newCount);
  }
);

const oddOrEven = computed(() => {
  if (counterData.count % 2 === 0) return "even";
  return "odd";
});

const add = (amount) => {
  counterData.count += amount;
};

const sub = (amount) => {
  counterData.count -= amount;
};
onMounted(() => {
  console.log("Do stuff related to Counter");
});
// onBeforeUpdate(() => {
//   console.log("onBeforeUpdate");
// });
// onUpdated(() => {
//   console.log("onUpdated");
// });
// onBeforeMount(() => {
//   console.log("onBeforeMount");
// });
// onMounted(() => {
//   console.log("onMounted");
// });
// onBeforeUnmount(() => {
//   console.log("onBeforeUnmount");
// });
// onUnmounted(() => {
//   console.log("onUnmounted");
// });
// onActivated(() => {
//   console.log("onActivated");
// });
// onDeactivated(() => {
//   console.log("onDeactivated");
// });
</script>

<style>
.home {
  text-align: center;
  padding: 20px;
}
.btn,
.counter {
  font-size: 40px;
  margin: 10px;
}
.edit {
  margin: 60px;
}
</style>
