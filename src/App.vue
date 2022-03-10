<template>
  <div class="fit__header">
    <h1 class="fit__header__title">Calcula tus macros</h1>
    <p class="fit__header__description">Ingresa tus datos y averigua cuántas proteínas, carbohidratos y grasas debes consumir en tu dieta.</p>
  </div>
  <form action="" class="fit__form">
  <fieldset class="fit__group fit__group--3-col">
    <h2 class="fit__group__label">Género</h2>
    <RadioInput v-model="gender" name="gender" value="female" :hasCheckIcon="false">Mujer</RadioInput>
    <RadioInput v-model="gender" name="gender" value="male" :hasCheckIcon="false">Hombre</RadioInput>
  </fieldset>
  <fieldset class="fit__group">
    <h2 class="fit__group__label">Edad</h2>
    <NumberInput v-model.number="age" name="age"/>
  </fieldset>
  <fieldset class="fit__group">
    <h2 class="fit__group__label">Peso</h2>
    <NumberInput v-model.number="weight" name="weight" suffix="kg" />
  </fieldset>
  <fieldset class="fit__group">
    <h2 class="fit__group__label">Talla</h2>
    <NumberInput v-model.number="height" name="height" suffix="cm" />
  </fieldset>
  <fieldset class="fit__group fit__group--3-col">
    <h2 class="fit__group__label">Nivel de Actividad Física</h2>
    <RadioInput v-model.number="activity" name="activity" value="1.2">
      <p>Sedentario</p>
      <small>Poco o nada de ejercicio.</small>
    </RadioInput>
    <RadioInput v-model.number="activity" name="activity" value="1.375">
      <p>Ligeramente Activo</p>
      <small>Ejercicio 1-2 días a la semana.</small>
    </RadioInput>
    <RadioInput v-model.number="activity" name="activity" value="1.55">
      <p>Moderadamente Activo</p>
      <small>Ejercicio 3-5 días a la semana.</small>
    </RadioInput>
    <RadioInput v-model.number="activity" name="activity" value="1.725">
      <p>Muy Activo</p>
      <small>Ejercicio 6-7 días a la semana.</small>
    </RadioInput>
    <RadioInput v-model.number="activity" name="activity" value="1.9">
      <p>Extremadamente Activo</p>
      <small>Ejercicio 6-7 días a la semana más un trabajo activo.</small>
    </RadioInput>
  </fieldset>
  <fieldset class="fit__group fit__group--3-col">
    <h2 class="fit__group__label">Objetivo</h2>
    <RadioInput v-model="objective" name="objective" value="definition">
      <p>Definición</p>
    </RadioInput>
    <RadioInput v-model="objective" name="objective" value="volume">
      <p>Volumen</p>
    </RadioInput>
  </fieldset>
  <button class="fit__btn" type="button" @click="printResult">Calcular</button>
  </form>
  <ResultsBox v-if="showResult" :results="printedResult"/>
</template>

<script>
import RadioInput from "./components/RadioInput.vue";
import NumberInput from "./components/NumberInput.vue";
import ResultsBox from "./components/ResultsBox.vue"

export default {
  name: "App",
  components: {
    RadioInput,
    NumberInput,
    ResultsBox,
  },
  data() {
    return {
      gender: 'male',
      weight: null,
      height: null,
      age: null,
      activity: 1.2,
      objective: 'definition',
      showResult: false,
      printedResult: {}
    };
  },
  computed: {
    macroResult() {
      let proteinValue, carbosValue, fatsValue, genderFactor;

      genderFactor = this.gender == 'male' ? 66 : 655;

      const caloriesSpending =
        this.activity *
        ((13.75 * this.weight) + (5 * this.height) - (6.76 * this.age) + genderFactor);

      if (this.objective == "definition") {
        proteinValue = (caloriesSpending * 0.45) / 4;
        carbosValue = (caloriesSpending * 0.35) / 4;
        fatsValue = (caloriesSpending * 0.2) / 9;
      } else if (this.objective == "volume") {
        proteinValue = (caloriesSpending * 0.4) / 4;
        carbosValue = (caloriesSpending * 0.4) / 4;
        fatsValue = (caloriesSpending * 0.2) / 9;
      }

      return {
        calories: Math.ceil(caloriesSpending),
        macros: [
          { name: "Proteínas", value: Math.ceil(proteinValue) },
          { name: "Carbohidratos", value: Math.ceil(carbosValue) },
          { name: "Grasas", value: Math.ceil(fatsValue) },
        ],
      };
    },
  },
  methods: {
    printResult() {
      this.showResult = true;
      this.printedResult = this.macroResult;
      this.$nextTick(() => {
        location.href = "#result"
      })
    }
  }
};
</script>

<style lang="scss">
* {
  box-sizing: border-box;
}

body {
  background-color: #f8fafc;
}

h1, h2, h3, h4, h5, h6 {
  margin: 0;
}

#app {
  font-family: "Ubuntu", sans-serif;
  max-width: 36rem;
  margin: 0 auto;
  color: #0f172a;
  padding: 0 1rem;
}

fieldset {
  margin: 0;
  padding: 0;
  border: none;
}

.fit__header {
  margin: 2rem 0 2rem 0;

  .fit__header__title {
    margin-bottom: 0.25rem;
  }

  .fit__header__description {
    line-height: 1.35;
    margin: 0;
  }
}


.fit__group__label {
  text-transform: uppercase;
  font-size: 0.85rem;
  margin-bottom: 0.66rem;
}

.fit__form {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-gap: 1.5rem 1rem;
}

.fit__group {
  &.fit__group--3-col {
    grid-column: span 3;
  }
}

.fit__btn {
  width: 100%;
  color: white;
  font-size: 1.25rem;
  padding: 1rem;
  border: none;
  border-radius: 0.25rem;
  background-color: #3b82f6;
}
</style>
