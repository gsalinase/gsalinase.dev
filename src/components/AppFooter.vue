<template>
  <footer class="footer">
    <small class="footer-content">
      <slot />
    </small>
  </footer>
</template>

<style lang="css" scoped>
.footer {
  width: 100%;
  background: var(--black);
}

.footer-content {
  display: block;
  padding: 3.3rem 0;
  text-align: center;
  font-size: var(--size-sm);
  color: var(--white);
}
</style>