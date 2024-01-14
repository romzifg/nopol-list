<template>
  <div class="w-full">
    <hr />
    <h1 class="flex justify-center font-bold mt-2 text-xl">
      Wilayah No Polisi
    </h1>
    <table class="mb-3">
      <tr>
        <th>No</th>
        <th>No Polisi</th>
        <th>Wilayah</th>
      </tr>
      <tr v-for="(no, i) in noPol" :key="i">
        <td>{{ i + 1 }}</td>
        <td>{{ no.nopol }}</td>
        <td>
          {{
            no.nopol.includes("KB")
              ? "Kalimantan Barat"
              : no.nopol.includes("AA")
              ? "Temanggung"
              : no.nopol.includes("B")
              ? "Jakarta"
              : no.nopol.includes("AD")
              ? "Surakarta"
              : ""
          }}
        </td>
      </tr>
    </table>
  </div>
</template>

<script setup>
defineProps({
  noPol: {
    type: Object,
    required: true,
  },
});
</script>
