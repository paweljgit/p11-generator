<template>
<div class="navigation-bar">
  <nav 
    class="navigation" 
    :style="numberOfDocuments> 0 ? 'justify-content: space-between' : 'justify-content: center'"
  >
    <div class="navigation__adding-section">
      <img src="../assets/growth.svg" v-if="numberOfDocuments===0" alt="Arrow" class="arrow">
      <BaseNavigationButton 
        @clickAction="$emit('addDocument')"
        :name="numberOfDocuments===0 ? 'Nowy formularz' : '+ Dodaj kolejny'" 
        :class="numberOfDocuments===0 ? 'button--add-new' : ''"
      />
      <BaseNavigationButton 
        @clickAction="$emit('open-modal')" 
        :name="'Import / Eksport'" 
      />  
    </div>
    <div v-if="numberOfDocuments>0">
      <BaseNavigationButton 
        v-if="numberOfDocuments>1"
        @clickAction="$emit('clearAllDocuments')" 
        :name="'Usuń wszystkie'" 
      />
      <BaseNavigationButton 
        @clickAction="$emit('generateReport')" 
        :name="numberOfDocuments>1 ? 'Drukuj (' + numberOfDocuments + ')': 'Drukuj'" 
      />
    </div>
  </nav>
</div>
</template>

<script>
import BaseNavigationButton from '../ui/BaseNavigationButton'

export default {
  name: 'TheNavigation',
  components: {
    BaseNavigationButton
  },
  props: {
    numberOfDocuments: {
      type: Number,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>
.navigation-bar {
  position: fixed;
  z-index: 5;
  top: 0px;
  text-align: center;
  background: linear-gradient(to bottom, #e63200, #fc4a1a);
  width: 100%;
}

.navigation {
  margin: 0 auto;
  width: 700px;
  display: flex;

  &__adding-section {
    position: relative;

    .button--add-new {
      font-size: 120%;
      padding: 15px 30px;
    }
  }
}

@keyframes look-here-animation {
  0% {
    top: 15px;
    left: -60px;
  }

  50% {
    top: 25px;
    left: -90px;
  }

  100% {
    top: 15px;
    left: -60px;
  }
}

.arrow {
  position: absolute;
  top: 15px;
  left: -60px;
  z-index: 50;
  width: 75px;
  height: 75px;
  transform: rotate(75deg);
  filter: invert(88%) sepia(71%) saturate(5355%) hue-rotate(326deg) brightness(98%) contrast(97%);
  animation: look-here-animation 2000ms infinite;
}
</style>
