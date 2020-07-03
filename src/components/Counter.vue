<template>
  <div>
    <i class="fab fa-4x" :class="icon"></i>
    <div class="counter" :data-target="{ target }">{{ initial }}</div>
    <h3>{{ description }}</h3>
  </div>
</template>

<script>
export default {
  name: 'Counter',
  props: ['icon', 'target', 'initial', 'description'],
};
</script>

<style lang="scss" scoped>
i {
  color: lightskyblue;
  margin-bottom: 5px;
}

.counter {
  font-size: 45px;
  margin: 10px 0;
}
</style>
