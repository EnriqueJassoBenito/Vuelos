<template>
  <div>
    <h1>AQUI ES VUELOS DISPONIBLES</h1>
    <b-breadcrumb :items="items"></b-breadcrumb>
    <b-link :to= "{name: 'lineasdevuelo'}">Siguiente</b-link>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          href: "#",
          to: { name: "lineasdevuelo" },
        },
      ],
    };
  },
};
</script>

<style>
</style>