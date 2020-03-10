<template>
  <div>
    <header>
      <div class="container container--max-width">
        <h1>Running Weather Dashboard</h1>
        <p>Going for a run? See how many layers you should put on!</p>
      </div>
    </header>
    <main class="container container--max-width">
      <article class="container__grid">
        <date-time :weather="weather" />
        <section>
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