<template>
<aside class="aside-bar">
  <div class="aside-bar__pages">
    <span class="numeration">
      <span class="numeration--big">{{ numberOfPages[0] }}</span> z {{ numberOfPages[1] }}
    </span>
  </div>
  <div class="aside-bar__options">
      <img 
        src="../assets/backspace.svg" 
        title="Wyczyść pola" 
        alt="Wyczyść pola" 
        class="icon-button" 
        @click="$emit('clear-button-clicked')"
      >
      <img 
        src="../assets/garbage-can.svg" 
        title="Usuń dokument" 
        alt="Usuń dokument" 
        class="icon-button" 
        @click="$emit('delete-button-clicked')"
      >
  </div> 
</aside>
</template>

<script>
export default {
  name: 'DocumentAside',
  props: {
    inputData: Object,
    numberOfPages: Array
  }
}
</script>


<style lang="scss" scoped>
.aside-bar {
  background-color: var(--base-primary-color);
  width: 100%;
  color: white;
  padding: 10px;
  border-radius: var(--base-border-radius);
  display: flex;
  justify-content: space-between;
  border: 1px solid rgba(0, 0, 0, 0.07);
  box-shadow: 0 8px 6px -6px rgba(0, 0, 0, 0.541);

  &__pages {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 75px;
    min-height: 100%;
    font-weight: bold;
    font-size: 120%;

    .numeration {
      display: block;
      text-align: center;
      width: 100%;

      &--big {
        display: inline;
        font-size: 140%;
      }
    }
  }

  &__options {
    text-align: right;

    .icon-button {
      width: 24px;
      height: 24px;
      cursor: pointer;
      filter: invert(99%) sepia(2%) saturate(116%) hue-rotate(190deg) brightness(117%) contrast(100%);
      transition: all .2s ease-in-out;

      &:hover {
        transform: scale(1.1)
      }

      &:last-of-type {
        margin-left: 10px;
      }
    }
  }
}
</style>
