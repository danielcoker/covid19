<template>
  <section class="w-11/12 lg:w-8/12 m-auto mt-16">
    <table class="w-full table-fixed">
      <thead>
        <tr>
          <th class="border w-1/4 px-4 py-2">State</th>
          <th class="border w-1/4 px-4 py-2">Confirmed</th>
          <th class="border w-1/4 px-4 py-2">Recovered</th>
          <th class="border w-1/4 px-4 py-2">Dead</th>
        </tr>
      </thead>
      <tbody v-if="states.length">
        <tr v-bind:key="state.location" v-for="state in states">
          <td class="border px-4 py-2">
            <router-link :to="{ name: 'State', params: { state: state.location } }">
              {{ state.location }}
            </router-link>
          </td>
          <td class="border px-4 py-2">{{ state.confirmed }}</td>
          <td class="border bg-green-700 text-white px-4 py-2">
            {{ state.recovered ? state.recovered : '--' }}
          </td>
          <td class="border bg-red-700 text-white px-4 py-2">
            {{ state.dead ? state.dead : '--' }}
          </td>
        </tr>
      </tbody>
      <p class="text-sm" v-else>Fetching Data...</p>
    </table>
  </section>
</template>

<script>
export default {
  name: 'ReportTable',
  props: ['states'],
};
</script>
