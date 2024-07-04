<script setup>
import init, { greeting, new_uuid, write_to_console, create_element } from "./pkg/example.js";
const rust = import('./pkg');

var name = ref("");
var uuid = ref("");

onBeforeMount(() => {
  console.log("app.vue - onBeforeMount: HELLO");
  init().then(() => {
    name.value = greeting();
    uuid.value = new_uuid();
  });
});

function change_uuid() {
  uuid.value = new_uuid();
}
</script>

<template>
  <div>
    <h2>Greeting: {{ name }}</h2>
    <h3>UUID: {{ uuid }}</h3>
    <div><button type="button" @click="change_uuid()">New UUID</button></div>
    <div><button type="button" @click="write_to_console()">Write to Console</button></div>
    <div><button type="button" @click="create_element()">Create Element</button></div>
  </div>
</template>