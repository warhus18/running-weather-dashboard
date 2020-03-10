<template>
  <div>
    <header class="header__container">
      <div class="container container--max-width">
        <div class="u-text-center header__inner">
          <h1 class="u-margin-hug-top u-margin-hug-bottom u-text-uppercase h3">Running Weather Dashboard</h1>
        </div>
      </div>
    </header>
    <main>
      <article class="container__grid container__grid--centered container__grid--max-xs">
        <section>
          <p>Going for a run? See how many layers you should put on!</p>
          <div>
            <label for="location-search">Enter Search Item</label>
            <input
              type="search"
              id="location-search"
              name="location-search"
              v-model="query"
              @keypress="fetchWeather"
            />
          </div>
        </section>
        <date-time :weather="weather" />
        <main-content :weather="weather" />
      </article>
    </main>
    <footer class="footer__container">
      <div class="footer__inner">
        <div class="container container--max-width">
          <p class="u-margin-hug-top u-margin-hug-bottom u-text-center">This application was designed and developed by Jessica Gidding.</p>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
import Content from '@/components/Content';
import Datetime from '@/components/DateTime';

export default {
  name: 'Dashboard',
  components: {
    'main-content': Content,
    'date-time': Datetime,
  },
  data() {
    return {
      api_key: 'b7b57a56024601cc847275029a5a73f5',
      url_base: 'https://api.openweathermap.org/data/2.5/',
      query: '',
      weather: {},
    };
  },
  methods: {
    fetchWeather(e) {
      if (e.keyCode === 13) {
        fetch(`${this.url_base}weather?q=${this.query}&units=imperial&APPID=${this.api_key}`)
          .then(res => (
            res.json()
          )).then(this.setResults);
      }
    },
    setResults(results) {
      this.weather = results;
    },
  },
};
</script>