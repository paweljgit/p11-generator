<template>
<div id="app">
  <TheNavigation 
    :numberOfDocuments="documents.length" 
    @addDocument="addDocument"
    @generateReport="generateReport"
    @clearAllDocuments="clearAllDocuments"
    @open-modal="toggleModal"
  />  
  <vue-html2pdf
    :show-layout="true"
    :float-layout="false"
    :enable-download="true"
    :preview-modal="false"
    :manual-pagination="true"
    :html-to-pdf-options="htmlToPdfOptions"
    @hasStartedGeneration="hasStartedGeneration()"
    @hasGenerated="hasGenerated($event)"
    pdf-content-width="fit-content"
    ref="html2Pdf"
    class="base-center-wrapper"
  >
    <section slot="pdf-content">
      <Document 
        v-for="(document, index) in documents" 
        :key="document.id"
        :id="'doc'+index"
        :inputData="documents[index]"
        :numberOfPages="[index+1, documents.length]"
        :documentIndex="index"
        :class="index != documents.length-1 ? 'html2pdf__page-break' : 'document--last'"
        @delete-button-clicked="deleteDocument(index)"
        @clear-button-clicked="clearDocumentFields(index)"
        @newValue="updateValueFromField"
      />
    </section>
  </vue-html2pdf> 
  <transition name="fade">
    <TheInstruction 
      v-if="documents.length == 0" 
    />
  </transition>
  <transition name="fade">
    <BaseModal 
      v-if="isModalOpen" 
      @close-modal="toggleModal"
    >
      <TheImportExportModal
        :currentData="documents"
        @close-modal="toggleModal"
        @import-data="importDataFromFile"
      />
    </BaseModal>
  </transition>
</div>
</template>

<script>
import TheNavigation from './components/TheNavigation'
import Document from './components/Document'
import VueHtml2pdf from 'vue-html2pdf'
import BaseModal from './ui/BaseModal'
import TheImportExportModal from './components/TheImportExportModal'
import TheInstruction from './components/TheInstruction'
import fieldsSetTemplate from './assets/data/fieldsSetTemplate.json'

export default {
  name: 'App',
  components: {
    TheNavigation, Document, VueHtml2pdf, BaseModal, TheImportExportModal, TheInstruction
  },
  data() {
    return {
      documents: [],
      htmlToPdfOptions: {
        margin: [20, 42, 0, 0],
        filename: 'potwierdzenie_nadania.pdf',
        image: {
          type: 'jpeg', 
          quality: 0.98
        },
        jsPDF: { unit: 'mm', format: 'a4', orientation: 'portrait' },
        html2canvas: {
          scrollX: 0, 
          scrollY: 0,
        }
      },
      fieldsSet: fieldsSetTemplate,
      isModalOpen: false,
    }
  },
  methods: {
    addDocument() {
      this.documents.push({"id": Math.random(), ...this.fieldsSet});   
      if (this.documents.length > 1) {  
        this.$nextTick( () =>
          this.$el.getElementsByClassName('document--last')[0].scrollIntoView(
            {behavior: 'smooth'}
          )
        )
      }
    },
    deleteDocument(index) {
      this.documents.splice(index, 1);
      if (index != 0) {
        const previousDocument = document.getElementById('doc'+ (index-1));
        this.$nextTick( () =>    
          previousDocument.scrollIntoView(
            {behavior: 'smooth'}
          )
        )
      }
    },
    clearAllDocuments() {
      this.documents = []
    },
    clearDocumentFields(index) {
      for (const key in this.fieldsSet) {
        this.documents[index][key] = ''
      }
    },
    updateValueFromField(value, field, index) {
      this.documents[index][field] = value;
    },
    generateReport() { 
      this.$refs.html2Pdf.generatePdf()
    },
    toggleModal() {
      this.isModalOpen = !this.isModalOpen
    },
    importDataFromFile(data) {
      this.documents = data
    }
  }
}
</script>
