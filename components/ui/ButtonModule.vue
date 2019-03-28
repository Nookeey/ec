<template>
  <button class="btn btn-remove" @click="$emit('removeModule')">X</button>
</template>

<script>
export default {
}
</script>

<style scoped>
  .btn {
    width: 40px;
    height: 40px;
    background: #ececec;
    color: #000;
    border: none;
    transition: all .3s ease;
  }

  .btn-remove:hover {
    background: tomato;
    color: #ffffff;
  }
</style>
