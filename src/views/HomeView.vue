<template>
  <div>
    <div>
    <table class="w-3/4 m-auto my-4 bg-white border border-gray-300">
      <thead class="bg-zinc-400">
        <tr>
          <th class="py-2 px-4 border-b">Cód</th>
          <th class="py-2 px-4 border-b">Nome</th>
          <th class="py-2 px-4 border-b">Máximo</th>
          <th class="py-2 px-4 border-b">Minimo</th>
          <th class="py-2 px-4 border-b">Variação</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(obj, key) in moedas" :key="key">
          <td class="py-2 px-4 text-center">{{ key }}</td>
          <td class="py-2 px-4 text-center">{{ obj.name }}</td>
          <td class="py-2 px-4 text-center">{{ obj.high }}</td>
          <td class="py-2 px-4 text-center">{{ obj.low }}</td>
          <td v-if="obj.varBid < 0" class="bg-red-600 bg text-center">{{ obj.varBid }}%</td>
          <td v-else class="py-2 bg-green-600 px-4 text-center">{{ obj.varBid }}%</td>
        </tr>
      </tbody>
    </table>
  </div>
      
  </div>
 </template>
 <script>
   import api from "../services/api";
 
   export default {
    name: "HomeView",
    data() {
      return {
        moedas: {},
      };
    },
    created() {
      this.getMoedas();
    },
    methods: {
      getMoedas() {
        api
          .get("/all")
          .then((res) => {
            this.moedas = res.data;
          })
          .catch((error) => {
            console.log(error);
          });
      },
    },
   };
 </script>