<template>
<section>
  <form class="confirmation-template">
    <section class="confirmation-template__adressess">

      <header>
        <h1 class="title">POTWIERDZENIE NADANIA <br />przesyłki poleconej nr</h1>
      </header>

      <fieldset class="address">
        <legend class="address__label">
          NADAWCA:
        </legend>
        <div class="address__fieldset">
          <input 
            type="text" 
            class="address__input" 
            id="senderAddressLine1" 
            ref="firstInput"
            :value="inputData.senderAddressLine1" 
            @change="fieldChange($event)"
          >
          <input 
            type="text" 
            class="address__input" 
            id="senderAddressLine2" 
            :value="inputData.senderAddressLine2" 
            @change="fieldChange($event)"
          >
          <input 
            type="text" 
            class="address__input" 
            id="senderAddressLine3" 
            :value="inputData.senderAddressLine3"
            @change="fieldChange($event)"
          >
          <div class="address__zip">
            <input 
              class="address__input address__input--zip" 
              type="text" 
              id="senderAddressZip"
              :value="inputData.senderAddressZip"
              @change="fieldChange($event)"
            >
            <label 
              class="address__input-label address__input-label--zip"
              for="senderAddressZip"
            >
              kod pocztowy
            </label>
          </div>
          <div class="address__city">
            <input 
              type="text" 
              class="address__input address__input--city" 
              id="senderAddressCity"
              :value="inputData.senderAddressCity"
              @change="fieldChange($event)"
            >
            <label 
              class="address__input-label address__input-label--city"
              for="senderAddressCity"
            >
              miejscowość
            </label>
          </div>
        </div>
      </fieldset>

      <fieldset class="address address--recipient">
        <legend class="address__label">
          ADRESAT:
        </legend>
        <div class="address__fieldset">
          <input 
            type="text" 
            class="address__input" 
            id="recipientAddressLine1" 
            :value="inputData.recipientAddressLine1" 
            @change="fieldChange($event)"
          >
          <input 
            type="text" 
            class="address__input" 
            id="recipientAddressLine2"
            :value="inputData.recipientAddressLine2" 
            @change="fieldChange($event)"
          >
          <input 
            type="text" 
            class="address__input" 
            id="recipientAddressLine3"
            :value="inputData.recipientAddressLine3" 
            @change="fieldChange($event)"
          >
          <div class="address__zip">
            <input 
              class="address__input address__input--zip" 
              type="text" 
              id="recipientAddressZip"
              :value="inputData.recipientAddressZip"
              @change="fieldChange($event)"
            >
            <label 
              class="address__input-label address__input-label--zip"
              for="recipientAddressZip"
            >
              kod pocztowy
            </label>
          </div>
          <div class="address__city">
            <input 
              type="text" 
              class="address__input address__input--city"
              id="recipientAddressCity"
              :value="inputData.recipientAddressCity"
              @change="fieldChange($event)"
            >
            <label 
              class="address__input-label address__input-label--city"
              id="recipientAddressCity"
            >
              miejscowość
            </label>
          </div>
        </div>
      </fieldset>

      <span class="section-info">
        Proszę odwrócić
      </span>

    </section>
    <section class="confirmation-template__options">

      <fieldset class="delivery-confirmation">
        <input type="checkbox" 
          id="deliveryConfirmation" 
          name="delivery-confirmation" 
          class="delivery-confirmation__checkbox"
          value="Tak"
          :checked="isChecked(inputData.deliveryConfirmation)"
          @change="checkboxChange($event)"
        >
        <label 
          for="deliveryConfirmation" 
          class="delivery-confirmation__label"
        >
          Potwierdzenie doręczenia albo zwrotu
        </label>
        <div class="break"></div>
        <label 
          class="delivery-confirmation__notification-label" 
          for="notification"
        >
          SMS/E-MAIL
        </label>
        <input 
          class="delivery-confirmation__notification-input" 
          id="notification"
          type="text"
          :value="inputData.notification" 
          @change="fieldChange($event)"
        >
      </fieldset>

      <div class="additional-options">
        <input 
          type="checkbox" 
          id="receiptConfirmation" 
          name="receipt-confirmation" 
          class="additional-options__receipt-confirmation-checkbox"
          value="Tak"
          :checked="isChecked(inputData.receiptConfirmation)"
          @change="checkboxChange($event)"
        >
        <label 
          for="receiptConfirmation" 
          class="additional-options__receipt-confirmation-label"
        >
          Potwierdzenie odbioru
        </label>
        <input 
          type="checkbox" 
          id="priority" 
          name="priority" 
          class="additional-options__priority-checkbox"
          value="Tak"
          :checked="isChecked(inputData.priority)"
          @change="checkboxChange($event)"
          >
        <label 
          for="priority" 
          class="additional-options__priority-label"
        >
          Priorytetowa
        </label>
      </div>

      <fieldset class="size">
        <input 
          class="size__checkbox" 
          type="checkbox" 
          id="sizeA" 
          name="A"
          value="Tak"
          :checked="isChecked(inputData.sizeA)"
          @change="checkboxChange($event)"
        >
        <label class="size__label" for="sizeA">
          A
        </label>
        <input 
          class="size__checkbox" 
          type="checkbox" 
          id="sizeB" 
          name="B"
          value="Tak"
          :checked="isChecked(inputData.sizeB)"
          @change="checkboxChange($event)"
        >
        <label class="size__label" for="sizeB">
          B
        </label>
        <legend class="size__legend">
          Gabaryt
        </legend>
      </fieldset>

      <div class="weight-and-charge">
        <fieldset class="weight">
          <legend class="weight__legend">
            Masa
          </legend>
          <input 
            class="weight__kg-input" 
            id="weightKg"
            type="text"
            :value="inputData.weightKg" 
            @change="fieldChange($event)"
          >
          <label class="weight__kg-label" for="weightKg">
            kg
          </label>
          <input 
            class="weight__g-input" 
            id="weightG"
            type="text"
            :value="inputData.weightG" 
            @change="fieldChange($event)"
          >
          <label class="weight__g-label" for="weightG">
            g
          </label>
        </fieldset>

        <fieldset class="charge">
          <legend class="charge__legend">
            Opłata
          </legend>
          <input 
            class="charge__zl-input" 
            id="chargeZl"
            type="text"
            :value="inputData.chargeZl" 
            @change="fieldChange($event)"
          >
          <label class="charge__zl-label" for="chargeZl">
            zł
          </label>
          <input 
            class="charge__gr-input" 
            id="chargeGr"
            type="text"
            :value="inputData.chargeGr" 
            @change="fieldChange($event)"
          >
          <label class="charge__gr-label" for="chargeGr">
            gr
          </label>
        </fieldset>
      </div>

      <div class="postage-stamp"></div>

      <p class="information">Na stronie <a href="https://sledzenie.poczta-polska.pl" target="_blank" >http://sledzenie.poczta-polska.pl</a> mozna sprawdzić status nadanej przesyłki rejestrowanej.</p>

      <div class="footer">
        <div class="footer__logo">
          <img src="../assets/pp-logo.svg" width="205px" height="34px" alt="Logo Poczta Polska">
          <p>PP S.A. nr <span class="strong">11</span></p>
        </div>
        <div class="footer__info">
          <p class="strong">PRZESYŁKA POLECONA</p>
          <span class="copy">Wydział Poligrafii PI Wrocław 2014</span>
        </div>
      </div>

    </section>
  </form>
</section>
</template>

<script>
export default {
  name: 'DocumentForm',
  data() {
    return {
    }
  },
  props: {
    inputData: Object,
    numberOfPages: Array
  },
  mounted() {
    setTimeout(() => this.$refs.firstInput.focus(), 750)
  },
  methods: {
    fieldChange(element) {
      this.$emit('form-updated', element.target.value, element.target.id);
    },
    isChecked(element) {
      if (element === "Tak" || element === "tak") {
        return true
      } else {
        return false
      }
    },
    checkboxChange (element) {
      if (element.target.checked) {
        this.$emit('form-updated', element.target.value, element.target.id);
      } else {
        this.$emit('form-updated', '', element.target.id);
      }
    }
  }
}
</script>


<style lang="scss" scoped>

.confirmation-template {
  background-color: white;
  // PIXEL PERFECT CHECK:
  // background-image: url(../assets/bg.png);
  // background-size: 470px;
  // background-position: top;
  // background-repeat: no-repeat;
  border: 1px solid black;
  width: 470px;
  position: relative;
  font-family: Arial, Helvetica, sans-serif;
  font-size: 13px;

  .section-info {
    font-size: 80%;
  }

  input {
    border: none;
    border-bottom: 2px rgb(0, 0, 0) dotted;
    line-height: 20px;
    background-color: transparent;
    &:focus {
      outline: 0 !important;
      background: rgb(223,223,223);
      background: linear-gradient(0deg, rgb(236, 236, 236) 0%, rgba(255,255,255,1) 100%);
    }
  }

  fieldset {
    margin-inline-start: 0px;
    margin-inline-end: 0px;
    padding-block-start: 0px;
    padding-inline-start: 0px;
    padding-inline-end: 0px;
    padding-block-end: 0px;
    min-inline-size: 0px;
    border: none;
  }

  legend {
    padding-inline-start: 0px;
    padding-inline-end: 0px;
    border-width: 0px;
    border-style: none;
    border-color: transparent;
    border-image: none;
    float: left;
  }
}

.confirmation-template__adressess,
.confirmation-template__options {
  padding-left: 20px;
  padding-right: 25px;
}

.confirmation-template__adressess {
  padding-top: 8px;
  border-bottom: 1px solid black;
  height: 337px;

  .title {
    font-size: 13.5px;
    line-height: 18px;
  }

  .address {
    display: flex;
    flex-flow: row nowrap;
    justify-content: flex-start;
    width: 100%;
    margin-top: -12px;
    margin-bottom: 5px;

    &--recipient {
      margin-top: 5px;
    }

    &__label {
      display: flex;
      max-width: 83px;
      min-width: 83px;
      flex-basis: auto;
      font-weight: bold;
      margin-top: 12px;
    }
    &__fieldset {
      display: flex;
      flex-wrap: wrap;
      flex-grow: 1;
    }

    &__input {
      height: 24px;
      margin-bottom: 5px;
      padding: 0px 10px;
      min-width: 100%;

      &--zip,
      &--city {
        margin-bottom: 0px;
      }
    }

    &__zip,
    &__city {
      display: flex;
      flex-direction: column;
    }

    &__zip {
      width: 95px;
      margin-right: 17px;
      flex-basis: auto;
    }

    &__city {
      flex-grow: 1;
    }

    &__input-label--zip,
    &__input-label--city {
      text-align: center;
      font-size: 85%;
    }
  }

  .section-info {
    font-size: 9.5px;
    display: block;
    font-style: italic;
    min-width: 100%;
    text-align: right;
  }
}

.confirmation-template__options {
  padding-top: 18px;
  font-size: 110%;
  height: 334px;

  input[type=checkbox] {
    position: relative;
    cursor: pointer;
    display: flex;
    width: 17px;
    height: 17px;
  }

  input[type=checkbox]:before {
    content: "";
    position: absolute;
    width: 17px;
    height: 17px;
    top: 0;
    left: 0;
    border: 1px solid #000;
    background-color: white;
  }

  input[type=checkbox]:checked:after {
    content: "";
    width: 7px;
    height: 10px;
    border: solid black;
    border-width: 0 2px 2px 0;
    -webkit-transform: rotate(45deg);
    -ms-transform: rotate(45deg);
    transform: rotate(45deg);
    position: absolute;
    top: 1px;
    left: 5px;
  }

  .delivery-confirmation {
    display: flex;
    width: 100%;
    flex-wrap: wrap;
    margin-bottom: 17px;

    &__checkbox {
      margin-right: 17px;
    }

    &__label {
      display: flex;
      align-self: flex-end;
      flex-grow: 1;
    }

    .break {
      min-width: 100%;
      height: 17px;
    }

    &__notification-label {
      align-self: flex-end;
      margin-right: 5px;
    }

    &__notification-input {
      display: flex;
      padding: 0px 10px;
      flex-grow: 1;
    }
  }
  .additional-options {
    display: flex;
    margin-bottom: 29px;

    &__receipt-confirmation-checkbox, &__priority-checkbox {
      margin-right: 10px;
    }

    &__receipt-confirmation-label {
      margin-right: 22px;
    }
  }
  .size {
    display: flex;
    margin-bottom: 21px;
    height: 20px;

    &__checkbox {
      margin-right: 10px;
    }

    &__label {
      margin-right: 29px;
      display: flex;
      align-items: flex-end;
    }

    &__legend {
      align-items: flex-end;
    }
  }

  .weight-and-charge {
    display: flex;
    justify-content: space-between;
    margin-bottom: 19px;

    .weight,
    .charge {
      display: flex;
      align-items: flex-end;
      height: 21px;
    }

    .weight__kg-input,
    .charge__zl-input {
      width: 65px;
      padding: 0px 10px;
      margin: 0px 5px;
      height: 18px;
      align-self: flex-start;
    }

    .weight__g-input,
    .charge__gr-input {
      width: 38px;
      padding: 0px 10px;
       margin: 0px 5px;
      height: 18px;
      align-self: flex-start;
    }
  }

  .information {
    font-size: 87%;
    line-height: 140%;
    margin-bottom: 5px;

    a {
      color: black
    }
  }

  .footer {
    display: flex;
    justify-content: space-between;

    &__logo {
      font-size: 87%;

      img {
        margin-bottom: 5px;
      }
    }

    &__info {
      display: flex;
      flex-wrap: wrap;
      padding-top: 12px;
      justify-content: flex-end;

      .copy {
        margin-top: -5px;
        font-size: 67%;
      }
    }

    .strong {
      font-weight: bold;
    }
  }
  
  .postage-stamp {
    width: 68px;
    height: 68px;
    border-radius: 35px;
    border: 1px solid black;
    display: block;
    position: absolute;
    bottom: 176px;
    right: 45px;
    z-index: 1;
  }
}
</style>
