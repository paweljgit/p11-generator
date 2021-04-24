<template>
<div class="import-export-modal">
  <h3 class="import-export-modal__header">Import i export</h3>
  <p class="import-export-modal__info">
    Mozesz wyeksportować przygotowane dokumenty w formacie json. Gdy wrócisz do aplikacji za jakiś czas to mozesz zaimportować ten plik i ponownie edytować/wydrukować dokumenty.
  </p>
  <div class="import-export-modal__wrapper">
    <div class="import-export-modal__element">
        <label>Dodaj plik json</label>
        <input 
          type="file" 
          accept="application/json" 
          @change="importData" 
        />
    </div>
    <div class="import-export-modal__element">
      <label>Eksportuj plik json</label>
      <button 
        v-if="currentData.length != 0" 
        @click="exportData"
        class="import-export-modal__button"
      >
        Zapisz
      </button>
      <button 
        v-else class="import-export-modal__button" 
        disabled
      >
        Zapisz
      </button>
    </div>
  </div>

</div>
</template>

<script>
export default {
  name: 'TheImportExportModal',
  props: {
    currentData: Array
  },
  methods: {
    importData(e) {
      const files = e.target.files || e.dataTransfer.files;
      if (!files.length) return;
      this.readFile(files[0]);
    },
    readFile(file) {
      const reader = new FileReader();
      reader.onload = e => {
        const json = JSON.parse(e.target.result);
        const jsonWithId = json.map( function (element) {
          element.id = Math.random();
          return element
        });
        this.$emit('import-data', jsonWithId);
        this.$emit('close-modal');
      };
      reader.readAsText(file);
    },
    exportData() {
      const dataClone = JSON.parse(JSON.stringify(this.currentData));
      const dataWithoutId = dataClone.map( function (element) {
        delete element.id;
        return element;
      });
      const data = JSON.stringify(dataWithoutId)
      const blob = new Blob([data], {type: 'text/plain'})
      const e = document.createEvent('MouseEvents'),
      a = document.createElement('a');
      a.download = "my-lovely-export.json";
      a.href = window.URL.createObjectURL(blob);
      a.dataset.downloadurl = ['text/json', a.download, a.href].join(':');
      e.initEvent('click', true, false, window, 0, 0, 0, 0, 0, false, false, false, false, 0, null);
      a.dispatchEvent(e);
    }
  }
}
</script>

<style lang="scss" scoped>

.import-export-modal {
  width: 400px;

  &__header {
    margin-bottom: 10px;
  }

  &__info {
    line-height: 150%;
  }

  &__wrapper {
    width: 100%;
    display: flex;
    margin-top: 20px;
  }

  &__element {
    width: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    padding: 10px 0px;

    &:first-child {
      border-right: var(--base-line-style);
      z-index: 2;
    }

    label {
      margin-bottom: 10px; 
    }

    input {
      color: transparent;
      width: 90px;
      margin: 0px;
      padding: 0px;
    }
  }
  
  &__button {
    padding: 0px 10px;
  }
}
</style>
