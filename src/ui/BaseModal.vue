<template>
<div class="modal">
  <div 
    class="modal__background" 
    @click="$emit('close-modal')"
  >
  </div>
  <div class="modal__body-wrapper">
    <div class="modal__body">
      <button 
        class="modal__close-button" 
        @click="$emit('close-modal')"
      >
      </button>
      <slot></slot>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'BaseModal'
}
</script>

<style lang="scss" scoped>

.modal {
  width: 100vw;
  height: 100vh;
  position: fixed;
  top: 0px;
  z-index: 6 !important;

  &__background, &__body-wrapper {
    position: absolute;
    width: 100%;
    height: 100%;
  }

  &__background {
    background: rgba( 0, 0, 0, 0.93 );
    z-index: 1;
  }

  &__body-wrapper {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  &__body {
    border-radius: var(--base-border-radius);
    padding: var(--base-padding);
    background-color: white;
    z-index: 2;
    position: relative;
  }

  &__close-button {
    --button-size: 36px;
    position: absolute;
    right: calc(-1*(var(--button-size))/2);
    top: calc(-1*(var(--button-size))/2);
    border-radius: 100%;
    width: var(--button-size);
    height: var(--button-size);
    cursor: pointer;
    border: none;
    background-color:var(--base-secondary-color);
    box-shadow: 2px 2px 4px #000000;
    transition: all .2s ease-in-out;

    &:before,&:after  {
      width: 65%;
      height: 4px;
      content: '';
      background-color: rgb(255, 255, 255);
      display: block;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: rotate(45deg) translate(-50%, -50%);
      transform-origin: top left;
    }

    &:after{
      transform: rotate(-45deg) translate(-50%, -50%);
    }
    
    &:hover{
      transform: scale(1.1) rotate(5deg);
      filter: brightness(0.95);;
    }
  }
}
</style>
