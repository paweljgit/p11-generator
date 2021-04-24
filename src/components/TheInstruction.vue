<template>
<div class="instruction">
  <h1 class="instruction__title">Potwierdzenie nadania <br />przesyłki listowej poleconej</h1>
  <h2 class="instruction__subtitle">Druk Poczty Polskiej formularz PP 11</h2>
  <hr />
  <div class="instruction__text">
  <p>Ten nieoficjalny generator powstał, żeby ułatwić klientom Poczty Polskiej samodzielne przygotowanie druku przed wizytą w urzędzie pocztowym.</p><p>Aplikacja online pozwala w łatwy sposób - bez żadnego dodatkowego oprogramowania - wypełnić i wydrukować formularz do formatu pdf. Umożliwia też eksport uzupełnionych w formularzu danych oraz ich ponowne wykorzystanie przyszłości.</p>
  <p>Aplikacja powstała w ramach niekomercyjnego projektu programistycznego. Nie jest zlecona, autoryzowana ani utrzymywana przez Pocztę Polską. Generator działa bezpiecznie w Twojej przeglądarce - dane nie są rejestrowane na żadnym serwerze. Pełen kod źródłowy aplikacji jest publiczny i dostępny pod <a href="https://github.com/paweljgit/p11-generator" target="_blank" rel="noopener">linkiem</a>.</p><p>Miłego dnia i przyjemnego korzystania.</p>
  </div>
</div>
</template>

<script>
export default {
  name: 'TheInstruction',
}
</script>

<style lang="scss" scoped>
.instruction {
  padding: var(--base-padding);
  padding-bottom: 60px;
  border-radius: var(--base-border-radius);
  background-color: white;
  margin: 0 auto;
  width: 500px;
  margin-top: 100px;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 50px 100px -20px, rgba(0, 0, 0, 0.3) 0px 30px 60px -30px;

  &__title {
    margin-top: 0px;
    padding: 0px;
    font-size: 22px;
    line-height: 125%;
  }

  &__subtitle {
    font-size: 16px;
  }

  hr {
    margin: 20px 0px;
    border-top: var(--base-line-style);
  }

  &__text {
    line-height: 150%;
    text-align: justify;
    text-justify: distribute;
    text-align-last: left;

    & p:first-of-type {
      font-weight: bold;
    }
    
    & p:last-of-type {
      float: right;
      font-style: italic;
    }
  }
}
</style>
