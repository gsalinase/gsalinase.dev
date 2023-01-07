<template>
  <div class="navigation">
    {{ props.items }}
  </div>
</template>

<script setup>
const props = defineProps({
  items: {
    type: Array,
    required: true,
    default: () => ([])
  }
})
</script>

<style lang="css" scoped>


@media screen and (min-width: 600px) {
  .navigation {
    position: sticky;
    top:0;
    left: 0;
    bottom: 0;
    min-width: 300px;
    max-height: 100vh;
    background-color: var(--red);
  }
}
</style>