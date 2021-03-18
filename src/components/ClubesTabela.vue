<template>
  <v-simple-table>
    <template v-slot:default>
      <thead>
        <tr>
          <th colspan="2" class="text-left">Clube</th>
          <th class="text-right">Pontos</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(clube, index) of clubes" :key="clube.id">
          <td>{{ index + 1 }}</td>
          <td>
            <v-avatar size="24">
              <img :src="clube.escudo" :alt="clube.nome" />
            </v-avatar>
            <span class="pl-2">{{ clube.nome }}</span>
          </td>
          <td class="text-right">{{ clube.pontos }}</td>
        </tr>
      </tbody>
    </template>
  </v-simple-table>
</template>

<script>
export default {
  name: "ClubesTabela",
  props: {
    clubes: {
      type: Array,
      required: true,
    },
  },
};
</script>