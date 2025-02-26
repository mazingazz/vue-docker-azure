<script lang="ts">
import { defineComponent, ref, reactive } from 'vue'
import {
  DxPolarChart,
  DxCommonSeriesSettings,
  DxSeries,
  DxExport,
  DxTooltip,
} from 'devextreme-vue/polar-chart'

import type { PropType } from 'vue'
import type { LineOptions } from '@/interface/common'

export default defineComponent({
  name: 'Spider',
  props: {
    Options: {
      type: Object as PropType<LineOptions>,
      default: () => ({}),
    },
  },
  components: {
    DxPolarChart,
    DxCommonSeriesSettings,
    DxSeries,
    DxExport,
    DxTooltip,
  },
  setup(context) {
    const fruitSources = [
      { value: 'apples', name: 'Apples' },
      { value: 'grapes', name: 'Grapes' },
      { value: 'lemons', name: 'Lemons' },
      { value: 'oranges', name: 'Oranges' },
    ]

    const productionData = [
      {
        arg: 'USA',
        apples: 4.21,
        grapes: 6.22,
        lemons: 0.8,
        oranges: 7.47,
      },
      {
        arg: 'China',
        apples: 3.33,
        grapes: 8.65,
        lemons: 1.06,
        oranges: 5,
      },
      {
        arg: 'Turkey',
        apples: 2.6,
        grapes: 4.25,
        lemons: 0.78,
        oranges: 1.71,
      },
      {
        arg: 'Italy',
        apples: 2.2,
        grapes: 7.78,
        lemons: 0.52,
        oranges: 2.39,
      },
      {
        arg: 'India',
        apples: 2.16,
        grapes: 2.26,
        lemons: 3.09,
        oranges: 6.26,
      },
    ]

    return {
      fruitSources,
      productionData,
    }
  },
})
</script>
<template>
  <div id="spider-demo">
    <DxPolarChart
      id="chart"
      :data-source="productionData"
      :use-spider-web="true"
      title="Fruit Production in 2010 (Millions of Tons)"
    >
      <DxCommonSeriesSettings type="line" />
      <DxSeries
        v-for="fruit in fruitSources"
        :key="fruit.value"
        :value-field="fruit.value"
        :name="fruit.name"
      />
      <DxExport :enabled="true" />
      <DxTooltip :enabled="true" />
    </DxPolarChart>
  </div>
</template>
<style lang="scss"></style>
