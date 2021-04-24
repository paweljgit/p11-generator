<template>
<button 
  @click="$emit('clickAction')" 
  class="button" 
>
  {{ name }}
</button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    name: {
      type: String,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>
.button {
  background-color: #000000;
  color: #fff;
  font-weight: bold;
  border-radius: var(--base-border-radius);
  padding: 10px 20px;
  border: none;
  outline: none;
  margin: 5px;

  &:hover {
    border-bottom: 3px solid white;
    border-right: 3px solid white;
    margin-right: 2px;
  }
  
  &:active {
    background-color: rgb(29, 29, 29);       
    border-bottom: 3px solid rgb(94, 94, 94);
    border-right: 3px solid rgb(94, 94, 94);
  }
}
</style>
