<template>
  <section v-if="typeof weather.main != 'undefined'">
    <h2>What to wear running</h2>
    <template v-if="typeof weather.main != 'undefined' && weather.main.temp < 30">
      <temp-below-freezing />
    </template>
    <template v-if="typeof weather.main != 'undefined'
      && weather.main.temp > 30 && weather.main.temp < 40">
      <temp-thirties />
    </template>
    <template v-if="typeof weather.main != 'undefined'
      && weather.main.temp > 40 && weather.main.temp < 50">
      <temp-forties />
    </template>
    <div v-if="typeof weather.main != 'undefined'
      && weather.main.temp > 50 && weather.main.temp < 60">
      <temp-fifties />
    </div>
    <template v-if="typeof weather.main != 'undefined'
      && weather.main.temp > 60 && weather.main.temp < 70">
      <temp-sixties />
    </template>
    <template v-if="typeof weather.main != 'undefined' && weather.main.temp > 70">
      <temp-seventies-above />
    </template>
  </section>
</template>

<script>
import BelowFreezing from '@/components/temperature/BelowFreezing';
import Thirties from '@/components/temperature/Thirties';
import Forties from '@/components/temperature/Forties';
import Fifties from '@/components/temperature/Fifties';
import Sixties from '@/components/temperature/Sixties';
import SeventiesAbove from '@/components/temperature/SeventiesAbove';

export default {
  props: ['weather'],
  components: {
    'temp-below-freezing': BelowFreezing,
    'temp-thirties': Thirties,
    'temp-forties': Forties,
    'temp-fifties': Fifties,
    'temp-sixties': Sixties,
    'temp-seventies-above': SeventiesAbove,
  },
};
</script>
