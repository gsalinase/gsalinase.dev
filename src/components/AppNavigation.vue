<template>
  <div class="navigation" :class="isNavigationOpen ? 'navigation-open' : null">
    <!-- Hamburger/close button -->
    <a class="navigation-toggle" href="#" @click.prevent.stop="toggleNav">
      <span class="navigation-bar bar-1"></span> 
      <span class="navigation-bar bar-2"></span>
      <span class="navigation-bar bar-3"></span>
    </a>

    <!-- Welcome message -->
    <div v-if="!isNavigationOpen" class="navigation-message">
      {{ welcomeMessage }}
    </div>

    <!-- list -->
    <div class="navigation-list-container" v-if="isNavigationOpen" >
      <ul class="navigation-list">
        <li v-for="item in props.items" :key="item.id" class="navigation-item">
          <!-- Links -->
          <a class="navigation-link" v-if="item.type === 'link'" href="#">{{ item.name }}</a>
        </li>
      </ul>
    </div>

    <!-- Nav footer -->
    <div class="navigation-footer">
      <div class="navigation-logo">
        <slot name="i18n-flag"></slot>
        
        <div class="navigation-footer-bottom">
          <slot name="logo"></slot>
        </div>
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
//const mq = ref(matchMedia('max', 600))

// Methods
const toggleNav = () => isNavigationOpen.value = !isNavigationOpen.value

// Expose variables and functions
defineExpose({
  isNavigationOpen,
  toggleNav,
})
</script>

<style lang="css" scoped>
.navigation {
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: sticky;
  top:0;
  left: 0;
  bottom: 0;
  padding: 0.5rem 1rem;
  background-color: var(--red);
}

.navigation-open {
  min-height: calc(-16px + 100vh);
}

.navigation-message {
  display: none;
  min-width: max-content;
  font-family: var(--motserrat);
  font-size: var(--size-md);
  color: var(--white);
  rotate: -90deg;
}

.navigation-toggle {
  display: flex;
  flex-direction: column;
  order: 3;
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

.navigation-list {
 list-style: none;
 padding-top: 2.5rem;
 padding-left: 0;
 font-size: var(--size-md);  
}

.navigation-list-container {
  order: 2;
  height: 100%;
  width: 100%;
  align-self: flex-start;
  justify-self: flex-start;
}

.navigation-item {
  letter-spacing: 1px;
  border-bottom: 1px solid white;
  padding-bottom: .4  rem;
  margin-bottom: .8rem;
}

.navigation-list {
  width: 60%;
}

.navigation-link {
  text-decoration: none;
  color: var(--white);
}

.navigation-footer {
  order: 1;
}

@media screen and (min-width: 600px) {
  .navigation {
    flex-direction: column;
    align-items: center;  
    padding: 1.5rem 0.5rem;
    max-height: calc(-48px + 100vh);
    justify-content: space-between;
  }

  .navigation-message {
    display: block;
    rotate: -90deg;
    order: 2;
  }

  .navigation-toggle {
    order: 1;
  }

  .navigation-open {
    padding-left: 1.9rem;
    align-items: flex-start; 
    min-width: 200px;
    min-height: inherit;
  }

  .navigation-list-container {
    display: flex;
    list-style: none;
  }

  .navigation-open .navigation-logo {
    margin-left: -12px;
  }

  .navigation-footer {
    order: 3;
  }
}

@media screen and (min-width: 768px) {
  .navigation-open {
    min-width: 300px;
  }
}
</style>