---
include: "*.vue"
title: Prefer Composition API over Options API in Vue components
tags: vue,typescript,javascript
---

Favor the Composition API (`<script setup>` or `setup()` function) instead of the Options API when writing new Vue components.

Bad – Options API component

```vue
<script>
export default {
  name: "Counter",
  data() {
    return {
      count: 0,
    }
  },
  methods: {
    increment() {
      this.count++
    },
  },
  mounted() {
    console.log(`The initial count is ${this.count}.`)
  },
}
</script>

<template>
  <button @click="increment">Count is: {{ count }}</button>
</template>
```

Good – Composition API component (`<script setup>`)

```vue
<script setup lang="ts">
import { ref, onMounted } from "vue"

const count = ref(0)

function increment() {
  count.value++
}

onMounted(() => {
  console.log(`The initial count is ${count.value}.`)
})
</script>

<template>
  <button @click="increment">Count is: {{ count }}</button>
</template>
```
