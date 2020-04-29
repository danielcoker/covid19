<template>
  <header class="h-auto py-10">
    <div class="uppercase">
      <h1 class="text-base">Nigeria Covid-19 Statistics</h1>
      <p class="text-xs">
        Last Updated: <br />
        {{ lastUpdated }}
      </p>
    </div>
    <form action="" v-on:submit.prevent="submit()" class="mt-6">
      <input
        class="shadow appearance-none border rounded
                w-8/12 py-2 px-3 text-gray-700 leading-tight
                focus:outline-none"
        type="search"
        name="search"
        v-model="stateInput"
        placeholder="Search for state"
      />
    </form>
  </header>
</template>

<script>
export default {
  name: 'TheHeader',
  props: ['lastUpdated'],
  data() {
    return {
      stateInput: '',
    };
  },
  methods: {
    submit() {
      this.$router.push({ name: 'State', params: { state: this.stateInput } }).catch((error) => {
        // eslint-disable-next-line no-console
        console.log(error);
      });
    },
  },
};
</script>
