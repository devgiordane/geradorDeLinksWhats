<template>
  <div class="col-12 py-5">
    <div class="form-group">
      <label for="">NÚMERO QUE RECEBERÁ AS MENSAGENS</label>
      <input
        type="text"
        v-model="numero"
        class="form-control"
        placeholder="+55 99 9 0000 0000"
      />
    </div>
    <div class="form-group">
      <label for="">MENSAGEM QUE O NÚMERO ESCOLHIDO RECEBERÁ</label>
      <textarea
        type="text"
        v-model="mensagem"
        class="form-control"
        placeholder="Opcional"
      />
    </div>
    <div
      v-show="showBtn"
      class="d-flex  justify-content-around align-items-center"
    >
      <div class="w-50 d-flex justify-content-center">
        <button @click="Geralink()" class="btn btn-success btn-block btn-lg">
          GERAR LINK
        </button>
      </div>
      <div class="w-50 d-flex justify-content-center">
        <button
          v-show="numero"
          @click="(numero = ''), (mensagem = '')"
          class="btn btn-danger btn-lg"
        >
          LIMPAR
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Gerador",
  data: function() {
    return {
      numero: "",
      mensagem: "",
      url: "",
      showBtn: false,
    };
  },
  methods: {
    Geralink: function() {
      let n = this.numero.replace(/[^0-9]/g, "");
      let m = encodeURI(this.mensagem);
      this.url = `https://wa.me/send?phone=${n}&text=${m}`;
      this.$router.push({
        name: "Resultado",
        params: {
          link: this.url,
        },
      });
    },
  },
  watch: {
    numero: function() {
      if (this.numero.replace(/[^0-9]/g, "").length >= 13) {
        this.showBtn = true;
      } else {
        this.showBtn = false;
      }
    },
  },
};
</script>
