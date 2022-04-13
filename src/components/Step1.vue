<template>
  <div>
    <h1>Hello There!</h1>
    <p>Let's buy some insurance. It is going to take only a few steps</p>
    <button @click="$emit('update-step', 1)">Start</button>
  </div>
</template>

<script>
export default {};
</script>
