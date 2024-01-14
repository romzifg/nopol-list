<template>
  <div class="w-full mb-3">
    <h1 class="flex justify-center font-bold mt-2 text-xl">List No Polisi</h1>
    <table class="mb-3">
      <tr>
        <th>No</th>
        <th>No Polisi</th>
      </tr>
      <tr v-for="(no, i) in noPol" :key="i">
        <td>{{ i + 1 }}</td>
        <td>{{ no.nopol }}</td>
      </tr>
    </table>
    <div class="flex flex-row justify-center gap-20">
      <button
        @click="checkFrek"
        class="bg-blue-400 p-2 hover:bg-blue-600 text-white rounded-md"
      >
        {{ compFrek ? "Hide" : "Show" }} Frekuensi
      </button>
      <button
        @click="openCloseWilayah"
        type="button"
        class="bg-yellow-400 p-2 hover:bg-yellow-600 text-white rounded-md"
      >
        {{ showWilayah ? "Hide" : "Show" }} Data Wilayah
      </button>
    </div>
  </div>
  <FrekNoPolComponent v-show="compFrek" :frekuensi="frekNoPol" />
  <Wilayah v-show="showWilayah" :noPol="noPol" />
</template>

<script setup>
import { ref } from "vue";
import FrekNoPolComponent from "./components/FrekNoPol.vue";
import Wilayah from "./components/Wilayah.vue";

const noPol = ref([
  { nopol: "KB 9234 KT" },
  { nopol: "AA 3245 TYC" },
  { nopol: "KB 9133 RE" },
  { nopol: "B 9234 TU" },
  { nopol: "AD 9124 GH" },
  { nopol: "AD 9004 YGU" },
  { nopol: "B 9277 IOB" },
  { nopol: "AA 1143 BN" },
  { nopol: "B 9234 TU" },
]);
const frekNoPol = ref([]);
const compFrek = ref(false);
const showWilayah = ref(false);

const checkFrek = () => {
  if (!compFrek.value) {
    let count = {};
    let arr = [];
    noPol.value.forEach((el) => {
      const code = el.nopol.split(" ");
      count[code[0]] = (count[code[0]] || 0) + 1;
    });

    const keys = Object.keys(count);
    keys.forEach((el) => {
      arr.push({
        [el]: count[el],
      });
    });

    arr.sort(function (a, b) {
      return Object.values(b) - Object.values(a);
    });
    frekNoPol.value = arr;
  } else {
    frekNoPol.value = [];
  }

  compFrek.value = !compFrek.value;
};

const openCloseWilayah = () => {
  showWilayah.value = !showWilayah.value;
};
</script>

<style>
table {
  border-collapse: collapse;
  width: 50%;
  margin: 20px auto;
}

th,
td {
  padding: 5px;
  text-align: center;
  border: 1px solid grey;
}

th {
  background-color: orange;
  color: #ececec;
}
</style>
