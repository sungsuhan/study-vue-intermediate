<template>
<div>
  <h1>Hello {{userName}}</h1>
  <p>{{message}}</p>
</div>
</template>

<script>
export default {
  data() {
    return {
      userName: 'sungsu',
      message: 'welcome vue3.0'
    }
  }
}
</script>

<style scoped>
.text-red{
  color: blue;
}
</style>
