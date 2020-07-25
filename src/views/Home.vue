<template>
  <div class="row">
    <Gerador />
  </div>
</template>

<script>
// @ is an alias to /src
import Gerador from "@/components/Gerador.vue";

export default {
  name: "Home",
  components: {
    Gerador,
  },
};
</script>
