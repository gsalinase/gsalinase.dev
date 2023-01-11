<template>
  <div class="navigation" :class="isNavigationOpen ? 'navigation-open' : null">
    <!-- Hamburger/close button -->
    <a class="navigation-toggle" href="#" @click.stop="toggleNav">
      <span class="navigation-bar bar-1"></span> 
      <span class="navigation-bar bar-2"></span>
      <span class="navigation-bar bar-3"></span>
    </a>

    <!-- Welcome message -->
    <div class="navigation-message">
      {{ welcomeMessage }}
    </div>

    <!-- Links -->
    <ul v-if="isNavigationOpen" class="navigation-list">
      <li class="navigation-item">{{ props.items }}</li>
    </ul>

    <div class="navigation-footer">
      <div class="navigation-logo">
        <slot name="logo"></slot>
      </div>
    </div>
  </div>
</template>

<script setup>
// Imports
import { ref } from 'vue'

// Props
const props = defineProps({
  items: {
    type: Array,
    required: true,
    default: () => ([])
  },
  welcomeMessage: {
    type: String,
    required: false,
    default: 'Default message!'
  }
})

// Variables
const isNavigationOpen = ref(false)

// Methods
const toggleNav = (e) => {
  console.log(e)
}

// Expose variables and functions
defineExpose({
  isNavigationOpen,
  toggleNav,
})
</script>

<style lang="css" scoped>
.navigation {
  display: flex;
  flex-direction: column;
  align-items: center;  
  padding: 2rem 1rem;
  background-color: var(--red);
}

.navigation-message {
  min-width: max-content;
  font-family: var(--motserrat);
  font-size: var(--size-md);
  color: var(--white);
  rotate: -90deg;
}

.navigation-toggle {
  display: flex;
  flex-direction: column;

}

.navigation-bar {
  display: inline-block;
  height: 3px;
  background-color: var(--white);
  margin-bottom: 6px;
}

.bar-1, 
.bar-3 {
  width: 1.2rem;
}

.bar-2 {
  width: 2rem;
}

.bar-3 {

}

@media screen and (min-width: 600px) {
  .navigation {
    position: sticky;
    top:0;
    left: 0;
    bottom: 0;
    max-height: calc(-64px + 100vh);
    justify-content: space-between;
  }

  .navigation-open {
    min-width: 200px;
  }
}

@media screen and (min-width: 768px) {
  .navigation {

  }

  .navigation-open {
    min-width: 300px;
  }
}
</style>