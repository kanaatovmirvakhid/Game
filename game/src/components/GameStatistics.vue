<script setup lang="ts">
import { ref, computed } from 'vue';
import type { Ref } from 'vue';

// Тип для описания одного параметра
interface IParameter {
  value: number;
  name: string;
}

// Тип для одной колонки (группа параметров)
interface IStatisticColumn {
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
  firstColumn: IStatisticColumn;
  secondColumn: IStatisticColumn;
}

// Создание реактивного массива
const statistics: Ref<IRow[]> = ref([
  {
    firstColumn: {
      GDP: {
        value: 100_000, // ВВП в миллиардах долларов
        name: 'ВВП (млрд $)',
      },
      inflation: {
        value: 2.5, // Инфляция в процентах
        name: 'Инфляция (%)',
      },
      unemployment: {
        value: 5.5, // Уровень безработицы в процентах
        name: 'Безработица (%)',
      },
      deficitSurplus: {
        value: -3, // Бюджетный дефицит/профицит в процентах от ВВП
        name: 'Бюджетный дефицит/профицит (% ВВП)',
      },
      debtBurden: {
        value: 60, // Долговая нагрузка в процентах от ВВП
        name: 'Долговая нагрузка (% ВВП)',
      },
    },
    secondColumn: {
      happiness: {
        value: 70, // Индекс счастья от 0 до 100
        name: 'Индекс счастья',
      },
      ecology: {
        value: 65, // Экологическое состояние от 0 до 100
        name: 'Экологическое состояние',
      },
      poverty: {
        value: 12, // Уровень бедности в процентах
        name: 'Уровень бедности (%)',
      },
      export: {
        value: 20_000, // Чистый экспорт в миллиардах долларов
        name: 'Чистый экспорт (млрд $)',
      },
      priceIndex: {
        value: 102, // Индекс потребительских цен (в процентах, базовый уровень 100)
        name: 'Индекс потребительских цен',
      },
    },
  },
]);

// Пример вычисляемого свойства
const lastYear = computed(() => statistics.value.length - 1);
</script>

<template>
    <div class="statistics">
      <div class="statistics__column">
        <div class="statistics__item" v-for="(item, index) in statistics[lastYear].firstColumn" v-bind:key="index">
          <div class="statistics__name">{{ item?.name }}</div>
          <div class="statistics__value">{{ item?.value }}</div>
        </div>
      </div>
      <div class="statistics__column">
        <div class="statistics__item" v-for="(item, index) in statistics[lastYear].secondColumn" v-bind:key="index">
          <div class="statistics__name">{{ item?.name }}</div>
          <div class="statistics__value">{{ item?.value }}</div>
        </div>
      </div>
    </div>
</template>

<style scoped lang="scss">
.statistics{
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 20px;
  margin: 0 auto;
  border: 1px solid #000000;
  border-top: 0;
  padding: 20px;
  border-radius: 0 0 10px 10px;
  &__column{
    width: 300px;
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
  &__item{
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 20px;
  }
}
</style>
