<template>
  <div class="font-sans w-full text-gray-700">
    <TheHeader v-bind:lastUpdated="lastUpdated" />
    <main>
      <section class="w-8/12 flex justify-between m-auto mt-10 uppercase">
        <div>
          <h3 class="font-extrabold">
            {{ summary.confirmed ? summary.confirmed : '--' }}
          </h3>
          <p class="text-xs">Confirmed</p>
        </div>
        <div>
          <h3 class="text-green-700 font-extrabold">
            {{ summary.recovered ? summary.recovered : '--' }}
          </h3>
          <p class="text-xs">Recovered</p>
        </div>
        <div>
          <h3 class="text-red-700 font-extrabold">{{ summary.dead ? summary.dead : '--' }}</h3>
          <p class="text-xs">Dead</p>
        </div>
      </section>

      <ReportTable v-bind:states="states" />
    </main>
    <footer class="mt-8">
      <p class="text-center text-gray-500 text-xs">
        &copy; Daniel Coker -
        <a href="https://twitter.com/danielcoker_" target="_blank">Twitter</a> |
        <a href="https://www.trackcorona.live/" target="_blank">TrackCorona</a> |
        <a href="https://www.cdc.gov/coronavirus/2019-ncov/index.html" target="_blank">Safety</a>
      </p>
    </footer>
  </div>
</template>

<script>
import ReportTable from '@/components/ReportTable.vue';
import TheHeader from '@/components/TheHeader.vue';
import axios from 'axios';
import TimeAgo from 'javascript-time-ago';
import en from 'javascript-time-ago/locale/en';

TimeAgo.addLocale(en);

const timeAgo = new TimeAgo('en-US');

export default {
  name: 'Home',
  components: {
    ReportTable,
    TheHeader,
  },
  data() {
    return {
      summary: {},
      states: [],
      stateInput: '',
      lastUpdated: '--',
    };
  },
  created() {
    document.title = 'Nigerian Covid-19 Statistics';
    // Get virus summary for Nigeria.
    axios
      .get('https://www.trackcorona.live/api/countries/NG')
      .then((response) => {
        const [summary] = response.data.data;
        this.summary = summary;

        this.lastUpdated = timeAgo.format(Date.parse(this.summary.updated));
      })
      .catch((error) => {
        /* eslint-disable-next-line no-console */
        console.log(error);
      });
    // Get summary for Nigerian states.
    axios
      .get('https://www.trackcorona.live/api/cities')
      .then((response) => {
        const cities = response.data.data;
        const nigerianStates = cities.filter((city) => city.country_code === 'ng');

        this.states = nigerianStates;
      })
      .catch((error) => {
        /* eslint-disable-next-line no-console */
        console.log(error);
      });
  },
};
</script>
