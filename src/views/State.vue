<template>
  <div class="font-sans w-full text-gray-700">
    <header class="h-auto py-10">
      <div class="uppercase">
        <h1 class="text-base">Nigeria Covid-19 Statistics</h1>
        <p class="text-xs">
          Last Updated: <br />
          {{ lastUpdated }}
        </p>
      </div>
    </header>
    <main>
      <h1 class="uppercase text-center text-3xl text-gray-700 text-extrabold">
        {{ state.location ? state.location : '--' }}
      </h1>
      <p class="uppercase text-xs">
        State
      </p>
      <section class="w-1/2 flex justify-between m-auto my-20 uppercase">
        <div>
          <h3 class="font-extrabold">{{ state.confirmed ? state.confirmed : '--' }}</h3>
          <p class="text-xs">Confirmed</p>
        </div>
        <div>
          <h3 class="font-extrabold">
            {{ state.confirmed ? state.confirmed - (state.recovered + state.dead) : '--' }}
          </h3>
          <p class="text-xs">Active</p>
        </div>
      </section>
      <section class="w-1/2 flex justify-between m-auto my-20 uppercase">
        <div>
          <h3 class="text-green-700 font-extrabold">
            {{ state.recovered ? state.recovered : '--' }}
          </h3>
          <p class="text-xs">Recovered</p>
        </div>
        <div>
          <h3 class="text-red-700 font-extrabold">{{ state.dead ? state.dead : '--' }}</h3>
          <p class="text-xs">Dead</p>
        </div>
      </section>
      <p>
        <!-- <a :href="{ name: 'Home' }">Go Back</a> -->
        <router-link :to="{ name: 'Home' }" class="uppercase text-xs">Go Home</router-link>
      </p>
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
import axios from 'axios';
import TimeAgo from 'javascript-time-ago';
import en from 'javascript-time-ago/locale/en';

TimeAgo.addLocale(en);

const timeAgo = new TimeAgo('en-US');

export default {
  name: 'About',
  data() {
    return {
      stateParam: this.$route.params.state,
      state: {},
      lastUpdated: '--',
    };
  },
  created() {
    axios
      .get(`https://www.trackcorona.live/api/cities/${this.stateParam}`)
      .then((response) => {
        const stateResults = response.data.data;
        const states = stateResults.filter(
          (stateResult) => stateResult.location.toLowerCase() === this.stateParam.toLowerCase(),
        );

        const [state] = states;
        this.state = state;

        this.lastUpdated = timeAgo.format(Date.parse(this.state.updated));
        document.title = `${this.state.location} - Nigeria Covid-19 Statistics`;
      })
      .catch((error) => {
        // eslint-disable-next-line no-console
        console.log(error);
      });
  },
};
</script>
