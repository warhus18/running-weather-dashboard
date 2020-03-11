<template>
  <section class="clothing-container__wrapper" v-if="typeof weather.main != 'undefined'">
    <div class="container container--max-width">
      <div class="clothing-container__inner">
        <h2 class="u-margin-hug-top u-text-center">What to wear running</h2>
        <!-- <div v-if="typeof weather.main != 'undefined' && weather.main.temp < 30">
          <temp-below-freezing />
        </div>
        <div v-if="typeof weather.main != 'undefined'
          && weather.main.temp > 30 && weather.main.temp < 40">
          <temp-thirties />
        </div>
        <div v-if="typeof weather.main != 'undefined'
          && weather.main.temp > 40 && weather.main.temp < 50">
          <temp-forties />
        </div>
        <div v-if="typeof weather.main != 'undefined'
          && weather.main.temp > 50 && weather.main.temp < 60">
          <temp-fifties />
        </div>
        <div v-if="typeof weather.main != 'undefined'
          && weather.main.temp > 60 && weather.main.temp < 70">
          <temp-sixties />
        </div>
        <div v-if="typeof weather.main != 'undefined' && weather.main.temp > 70">
          <temp-seventies-above />
        </div> -->

          <ol class="u-list-unstyled container__grid container__grid--3col clothing-list__container">
            <li class="clothing-list__item" v-for="item in clothingItems" v-bind:key="item">
              <div class="u-text-center">
                <div class="clothing-list__img">
                  <img src="https://via.placeholder.com/100x100" srcset="https://via.placeholder.com/100x100 1x, https://via.placeholder.com/200x200  2x" alt="Alternative Text Describing the Image">
                </div>
                <span class="clothing-list__text">{{ item.text }}</span>
              </div>
            </li>
            <!-- /. clothing-list__item -->
          </ol>
          <!-- /.clothing-list__container -->
      </div>
    </div>
  </section>
  <!-- /.clothing-container__wrapper -->
</template>

<script>
// import BelowFreezing from '@/components/temperature/BelowFreezing';
// import Thirties from '@/components/temperature/Thirties';
// import Forties from '@/components/temperature/Forties';
// import Fifties from '@/components/temperature/Fifties';
// import Sixties from '@/components/temperature/Sixties';
// import SeventiesAbove from '@/components/temperature/SeventiesAbove';

import clothing from '@/assets/clothing.json';

export default {
  props: ['weather'],
  data() {
    return {
      clothingItems: clothing
    }
  }
  
  // components: {
  //   'temp-below-freezing': BelowFreezing,
  //   'temp-thirties': Thirties,
  //   'temp-forties': Forties,
  //   'temp-fifties': Fifties,
  //   'temp-sixties': Sixties,
  //   'temp-seventies-above': SeventiesAbove,
  // },
};
</script>
