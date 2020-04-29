<template>
  <div class="font-sans w-full text-gray-700">
    <header class="h-auto py-10">
      <div class="uppercase">
        <h1 class="text-base">Nigeria Covid-19 Statistics</h1>
        <p class="text-xs">
          Last Updated: <br />
          6 minutes ago.
        </p>
      </div>
      <form action="" class="mt-6">
        <input
          class="shadow appearance-none border rounded
                w-8/12 py-2 px-3 text-gray-700 leading-tight
                focus:outline-none"
          type="search"
          name="search"
          placeholder="Search for state"
        />
      </form>
    </header>
    <main>
      <section class="w-8/12 flex justify-between m-auto mt-10 uppercase">
        <div>
          <h3 class="font-extrabold">1,998</h3>
          <p class="text-xs">Confirmed</p>
        </div>
        <div>
          <h3 class="text-green-700 font-extrabold">200</h3>
          <p class="text-xs">Recovered</p>
        </div>
        <div>
          <h3 class="text-red-700 font-extrabold">20</h3>
          <p class="text-xs">Dead</p>
        </div>
      </section>

      <section class="w-11/12 m-auto mt-16">
        <table class="table-fixed">
          <thead>
            <tr>
              <th class="border w-1/4 px-4 py-2">State</th>
              <th class="border w-1/4 px-4 py-2">Confirmed</th>
              <th class="border w-1/4 px-4 py-2">Recovered</th>
              <th class="border w-1/4 px-4 py-2">Dead</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td class="border px-4 py-2">Lagos</td>
              <td class="border px-4 py-2">500</td>
              <td class="border bg-green-700 text-white px-4 py-2">858</td>
              <td class="border bg-red-700 text-white px-4 py-2">858</td>
            </tr>
            <tr>
              <td class="border px-4 py-2">Kaduna</td>
              <td class="border px-4 py-2">500</td>
              <td class="border bg-green-700 text-white px-4 py-2">858</td>
              <td class="border bg-red-700 text-white px-4 py-2">858</td>
            </tr>
            <tr>
              <td class="border px-4 py-2">Kaduna</td>
              <td class="border px-4 py-2">500</td>
              <td class="border bg-green-700 text-white px-4 py-2">858</td>
              <td class="border bg-red-700 text-white px-4 py-2">858</td>
            </tr>
            <tr>
              <td class="border px-4 py-2">Lagos</td>
              <td class="border px-4 py-2">500</td>
              <td class="border bg-green-700 text-white px-4 py-2">858</td>
              <td class="border bg-red-700 text-white px-4 py-2">858</td>
            </tr>
            <tr>
              <td class="border px-4 py-2">Lagos</td>
              <td class="border px-4 py-2">500</td>
              <td class="border bg-green-700 text-white px-4 py-2">858</td>
              <td class="border bg-red-700 text-white px-4 py-2">858</td>
            </tr>
            <tr>
              <td class="border px-4 py-2">Kano</td>
              <td class="border px-4 py-2">500</td>
              <td class="border bg-green-700 text-white px-4 py-2">858</td>
              <td class="border bg-red-700 text-white px-4 py-2">858</td>
            </tr>
            <tr>
              <td class="border px-4 py-2">FCT</td>
              <td class="border px-4 py-2">500</td>
              <td class="border bg-green-700 text-white px-4 py-2">858</td>
              <td class="border bg-red-700 text-white px-4 py-2">858</td>
            </tr>
            <tr>
              <td class="border px-4 py-2">Ondo</td>
              <td class="border px-4 py-2">500</td>
              <td class="border bg-green-700 text-white px-4 py-2">858</td>
              <td class="border bg-red-700 text-white px-4 py-2">858</td>
            </tr>
            <tr>
              <td class="border px-4 py-2">Osun</td>
              <td class="border px-4 py-2">500</td>
              <td class="border bg-green-700 text-white px-4 py-2">858</td>
              <td class="border bg-red-700 text-white px-4 py-2">858</td>
            </tr>
          </tbody>
        </table>
      </section>
    </main>
    <footer class="mt-8">
      <p class="text-center text-gray-500 text-xs">
        &copy; Daniel Coker - <a href="https://twitter.com/danielcoker_" target="_blank">Twitter</a>
      </p>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'Home',
};
</script>
