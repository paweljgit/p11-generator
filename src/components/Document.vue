<template>
<div>
  <div class="separator"></div>
  <section class="pdf-item">
    <div class="aside-wrapper">
      <DocumentAside 
        :numberOfPages="numberOfPages" 
        @delete-button-clicked="$emit('delete-button-clicked')"
        @clear-button-clicked="$emit('clear-button-clicked')"
        data-html2canvas-ignore="true"
      />
    </div>
    <div class="document-wrapper">
      <div class="under-under-document hide-from-print"></div>
      <div class="under-document hide-from-print"></div>
        <DocumentForm 
          class="document"
          :inputData="inputData" 
          @form-updated="addIndexToValue"
        />
    </div>
  </section>
</div>
</template>

<script>
import DocumentAside from './DocumentAside'
import DocumentForm from './DocumentForm'

export default {
  name: 'Document',
  components: {
    DocumentAside, DocumentForm
  },
  props: {
    inputData: Object,
    numberOfPages: Array,
    documentIndex: Number,
  },
  methods: {
    addIndexToValue (value, filed) {
      this.$emit('newValue', value, filed, this.documentIndex);
    }
  }
}
</script>

<style lang="scss" scoped>

.separator {
  height: 100px;
}

.pdf-item {
  position: relative;
  width: 493px;
  height: 694px;
}

.aside-wrapper {
  position: sticky;
  width: 690px;
  top: 0px;
  margin-left: -100px;
  z-index: 0;
  padding-top: 70px;
  padding-bottom: 160px;
}

.document-wrapper {
  position: absolute;
  top: 0px;
  width: 100%;
  height: 100%;
  
  .under-under-document,
  .under-document,
  .document {
    width: 100%;
    height: 100%;
    background-color: white;
    box-shadow: 0 8px 6px -6px black;
    border: 1px solid rgb(233, 233, 233);
  }

  @keyframes rotate-right2deg-animation {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(2deg);
    }
  }

  @keyframes rotate-right4deg-animation {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(4deg);
    }
  }

  .under-under-document {
    position: absolute;
    animation: rotate-right4deg-animation 2000ms;
    animation-fill-mode: forwards;
  }

  .under-document {
    position: absolute;
    animation: rotate-right2deg-animation 2000ms;
    animation-fill-mode: forwards;
  }

  .document {
    position: relative;
    padding: 10px;
  }
}

</style>
