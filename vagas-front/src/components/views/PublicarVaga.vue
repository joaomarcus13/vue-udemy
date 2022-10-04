<template>
  <div class="container py-4">
    <div class="row">
      <div class="co">
        <h4>Apresente a sua vaga para milhares de profissionais</h4>
      </div>
    </div>
    <div class="row mt-3">
      <div class="col">
        <label class="form-label">Titulo da vaga</label>
        <input type="text" class="form-control" v-model="titulo" />
        <div class="form-text">Por exemplo: Programador JavaScript</div>
      </div>
    </div>
    <div class="row mt-3">
      <div class="col">
        <label class="form-label">Descricao</label>
        <textarea type="text" class="form-control" v-model="descricao" />
        <div class="form-text">Informe os detalhes da vaga</div>
      </div>
    </div>
    <div class="row mt-3">
      <div class="col">
        <label class="form-label">Salario</label>
        <input type="number" class="form-control" min="0" v-model="salario" />
        <div class="form-text">Informe o salario</div>
      </div>
      <div class="col">
        <label class="form-label">Modalidade</label>
        <select class="form-select ml-3" v-model="modalidade">
          <option value="" disabled>Selecione</option>
          <option value="1">Home Office</option>
          <option value="2">Presencial</option>
        </select>
        <div class="form-text">Informe a modalidade</div>
      </div>
      <div class="col">
        <label class="form-label">Tipo</label>
        <select class="form-select ml-3" v-model="tipo">
          <option value="" disabled>Selecione</option>
          <option value="1">CLT</option>
          <option value="2">PJ</option>
        </select>
        <div class="form-text">Informe o tipo de contratacao</div>
      </div>
    </div>
    <div class="row mt-3">
      <div class="col">
        <button type="submit" @click="salvarVaga" class="btn btn-primary">
          Cadastrar
        </button>
      </div>
    </div>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  name: 'PublicarVaga',
  data: () => ({
    titulo: '',
    descricao: '',
    salario: '',
    modalidade: '',
    tipo: '',
  }),
  methods: {
    salvarVaga() {
      this.validaForm();
      let vagas = JSON.parse(localStorage.getItem('vagas'));
      if (!vagas) vagas = [];
      vagas.push({
        titulo: this.titulo,
        descricao: this.descricao,
        salario: this.salario,
        modalidade: this.modalidade,
        tipo: this.tipo,
        publicacao: new Date().toISOString(),
      });
      if (this.validaForm()) {
        localStorage.setItem('vagas', JSON.stringify(vagas));
        this.emitter.emit('alerta', {
          titulo: `A vaga ${this.titulo} foi cadastrada com sucesso`,
          descricao: `a vaga foi cadastrada`,
          status: 'alert-success',
        });
        this.resetaFormulario();
      } else {
        this.emitter.emit('alerta', {
          titulo: `Nao foi possivel cadastrar`,
          descricao: `preencha todos os campos`,
          status: 'alert-warning',
        });
      }
    },
    validaForm() {
      let valida = true;
      valida = !Object.values(this.$data)
        .map((e) => e == '')
        .reduce((acc, v) => acc || v);
      return valida;
    },
    resetaFormulario() {
      this.titulo = '';
      this.descricao = '';
      this.salario = '';
      this.modalidade = '';
      this.tipo = '';
    },
  },
};
</script>
