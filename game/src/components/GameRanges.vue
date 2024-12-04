<script setup lang="ts">
import { ref } from 'vue';
import type { Ref } from 'vue';

// Тип для описания одного параметра
interface IParameter {
  value: number;
  name: string;
}

// Тип для одной колонки (группа параметров)
interface IRangeColumn {
  GDP?: IParameter;
  inflation?: IParameter;
  unemployment?: IParameter;
  deficitSurplus?: IParameter;
  debtBurden?: IParameter;
  happiness?: IParameter;
  ecology?: IParameter;
  poverty?: IParameter;
  export?: IParameter;
  priceIndex?: IParameter;
}

// Тип для строки статистики с двумя колонками
interface IRow {
  firstColumn?: IRangeColumn;
  secondColumn?: IRangeColumn;
  thirdColumn?: IRangeColumn;
  fourthColumn?: IRangeColumn;
}

// Создание реактивного массива
const ranges: Ref<IRow[]> = ref([
  {
    firstColumn: {
      taxRate: {
        value: 20, // Налоговая ставка
        name: 'Налоговая ставка',
      },
      governmentSpending: {
        value: 50, // Государственные расходы
        name: 'Государственные расходы',
      },
      loanRate: {
        value: 5, // Ставка по кредитам
        name: 'Ставка по кредитам',
      },
      minimumWage: {
        value: 30, // Минимальная зарплата
        name: 'Минимальная зарплата',
      },
      tradeBalance: {
        value: 10, // Экспорт и импорт
        name: 'Экспорт и импорт',
      },
    },
    secondColumn: {
      subsidyPrograms: {
        value: 40, // Программы субсидий
        name: 'Программы субсидий',
      },
      energyPolicy: {
        value: 50, // Энергетическая политика
        name: 'Энергетическая политика',
      },
      agriculture: {
        value: 30, // Сельское хозяйство
        name: 'Сельское хозяйство',
      },
      technologyInvestment: {
        value: 20, // Инвестиции в технологии
        name: 'Инвестиции в технологии',
      },
      transportInfrastructure: {
        value: 60, // Транспортная инфраструктура
        name: 'Транспортная инфраструктура',
      },
    },
    thirdColumn: {
      healthcare: {
        value: 40, // Здравоохранение
        name: 'Здравоохранение',
      },
      education: {
        value: 50, // Образование
        name: 'Образование',
      },
      militarySpending: {
        value: 20, // Военные расходы
        name: 'Военные расходы',
      },
      pensionRate: {
        value: 5, // Ставка по пенсионным накоплениям
        name: 'Ставка по пенсионным накоплениям',
      },
      consumerLoans: {
        value: 15, // Потребительские кредиты
        name: 'Потребительские кредиты',
      },
    },
    fourthColumn: {
      propertyTax: {
        value: 10, // Налог на имущество
        name: 'Налог на имущество',
      },
      pensionReform: {
        value: 20, // Пенсионная реформа
        name: 'Пенсионная реформа',
      },
      currencyRate: {
        value: 70, // Валютный курс
        name: 'Валютный курс',
      },
      cultureAndArts: {
        value: 30, // Культура и искусство
        name: 'Культура и искусство',
      },
      antiCorruption: {
        value: 50, // Борьба с коррупцией
        name: 'Борьба с коррупцией',
      },
    },
  },
]);

</script>

<template>
  <div class="range">
    <div class="range__column">
      <div
        class="range__item"
        v-for="(item, key) in ranges[0]?.firstColumn"
        v-bind:key="key"
      >
        <q-badge color="secondary">
          {{ item?.name }}: {{ item?.value }}
        </q-badge>
        <q-slider
          v-model="ranges[0].firstColumn[key].value"
          :min="0"
          :max="100"
          :step="1"
          label
          color="light-green"
        />
      </div>
    </div>
    <div class="range__column">
      <div
        class="range__item"
        v-for="(item, key) in ranges[0]?.secondColumn"
        v-bind:key="key"
      >
        <q-badge color="secondary">
          {{ item?.name }}: {{ item?.value }}
        </q-badge>
        <q-slider
          v-model="ranges[0].secondColumn[key].value"
          :min="0"
          :max="100"
          :step="1"
          label
          color="light-green"
        />
      </div>
    </div>
    <div class="range__column">
      <div
        class="range__item"
        v-for="(item, key) in ranges[0]?.thirdColumn"
        v-bind:key="key"
      >
        <q-badge color="secondary">
          {{ item?.name }}: {{ item?.value }}
        </q-badge>
        <q-slider
          v-model="ranges[0].thirdColumn[key].value"
          :min="0"
          :max="100"
          :step="1"
          label
          color="light-green"
        />
      </div>
    </div>
    <div class="range__column">
      <div
        class="range__item"
        v-for="(item, key) in ranges[0]?.fourthColumn"
        v-bind:key="key"
      >
        <q-badge color="secondary">
          {{ item?.name }}: {{ item?.value }}
        </q-badge>
        <q-slider
          v-model="ranges[0].fourthColumn[key].value"
          :min="0"
          :max="100"
          :step="1"
          label
          color="light-green"
        />
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.range{
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 30px;
  &__column{
    width: 100%;
    display: flex;
    flex-direction: column;
    gap: 20px;
  }
}
</style>
