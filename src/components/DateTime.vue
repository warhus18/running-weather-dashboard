<template>
  <section>
    <div v-if="typeof weather.main != 'undefined'">
      <div class="temperature__container">
        <div class="container container--max-width">
          <p>{{ Math.round(weather.main.temp) }} °F</p> <!-- temperature -->
          <p>{{ weather.weather[0].main }}</p> <!-- weather description -->
        </div>
      </div>
      <!-- /.temperature__container -->
      <div class="location__container">
        <div class="container container--max-width">
          <p>{{ weather.name }}</p> <!-- location -->
          <p><time datetime="">{{ dateBuilder() }}</time></p>
        </div>
      </div>
      <!-- /.ocation__container -->
    </div>
  </section>
</template>

<script>
export default {
  props: ['weather'],
  methods: {
    dateBuilder() {
      const d = new Date();
      const months = ['January', 'February', 'March', 'April', 'May', 'June',
        'July', 'August', 'Septempber', 'October', 'November', 'December'];
      const days = ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday',
        'Friday', 'Saturday'];

      const day = days[d.getDay()];
      const date = d.getDate();
      const month = months[d.getMonth()];
      const year = d.getFullYear();

      return `${day} ${date} ${month} ${year}`;
    },
  },
};
</script>