<template>
  <div class="card">
    <div class="card-header bg-dark text-white">
      <div class="row">
        <div class="col d-flex justify-content-between">
          <div>{{ titulo }}</div>
          <div>
            <div class="form-check form-switch">
              <input type="checkbox" class="form-check-input" v-model="favoritada">
              <label class="form-check-label">Favoritar</label>
            </div>
          </div>
        </div>
      </div>
      
    </div>
    <div class="card-body">
      <p>{{ descricao }}</p>
    </div>
    <div class="card-footer">
      <small class="text-muted"
        >Salário: R$ {{ salario }} | Modalidade: {{ getModalidade }} | Tipo:
        {{ getTipo }} | Publicação: {{ getPublicacao }}</small
      >
    </div>
  </div>
</template>

<script>

export default {
  name: 'VagaComponent',
  data: ()=>({
    favoritada: false,
  }), 
  watch:{
    favoritada(valorNovo){
      if(valorNovo){
        this.emitter.emit('favoritarVaga',this.titulo)
      }else{
        this.emitter.emit('desfavoritarVaga',this.titulo)
      }
    }
  },
  //props: ['tituloVagaTeste', 'descricaoVaga', 'salario', 'modalidade', 'tipo', 'publicacao'],
  props: {
    titulo: {
      type: String,
      required: true,
      validator(p) {
        //console.log('Prop: ', p, )
        if (p.length < 6) return false; //se estiver inválido
        return true; //se estiver válido
      },
    },
    descricao: {
      type: String,
      default: 'sem descricao',
    },
    salario: {
      type: [Number, String],
      required: true,
    },
    modalidade: {
      type: String,
      required: true,
    },
    tipo: {
      type: String,
      required: true,
    },
    publicacao: {
      type: String,
      required: true,
    },
  },
  computed: {
    getModalidade() {
      const modalidade = { 1: 'Home Office', 2: 'Presencial' };
      return modalidade[this.modalidade];
    },
    getTipo() {
      const tipo = { 1: 'CLT', 2: 'PJ' };
      return tipo[this.tipo];
    },
    getPublicacao() {
      return new Date(this.publicacao).toLocaleDateString();
    },
  },
  methods:{
    dispararEventoComMitt(){
      this.emitter.emit('eventoGlobal','teste')
    }
  }
};
</script>
