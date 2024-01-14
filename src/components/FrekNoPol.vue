<template>
  <div class="w-full">
    <hr />
    <h1 class="flex justify-center font-bold mt-2 text-xl">
      Frekuensi No Polisi
    </h1>
    <table class="mb-3">
      <tr>
        <th>No</th>
        <th>No Polisi</th>
        <th>Total</th>
      </tr>
      <tr v-for="(no, i) in frekuensi" :key="i">
        <td>{{ i + 1 }}</td>
        <td>{{ Object.keys(no)[0] }}</td>
        <td>{{ Object.values(no)[0] }}</td>
      </tr>
    </table>
  </div>
</template>

<script setup>
defineProps({
  frekuensi: {
    type: Object,
    required: false,
  },
});
</script>
