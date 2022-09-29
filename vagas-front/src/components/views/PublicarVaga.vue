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
        <input type="text" class="form-control" />
        <div class="form-text">Por exemplo: Programador JavaScript</div>
      </div>
    </div>
    <div class="row mt-3">
      <div class="col">
        <label class="form-label">Descricao</label>
        <textarea type="text" class="form-control" />
        <div class="form-text">Informe os detalhes da vaga</div>
      </div>
    </div>
    <div class="row mt-3">
      <div class="col">
        <label class="form-label">Salario</label>
        <input type="number" class="form-control" />
        <div class="form-text">Informe o salario</div>
      </div>
      <div class="col">
        <label class="form-label">Modalidade</label>
        <select class="form-select ml-3">
          <option value="1">Home Office</option>
          <option value="2">Presencial</option>
        </select>
        <div class="form-text">Informe a modalidade</div>
      </div>
      <div class="col">
        <label class="form-label">Tipo</label>
        <select class="form-select ml-3">
          <option value="1">CLT</option>
          <option value="2">PJ</option>
        </select>
        <div class="form-text">Informe o tipo de contratacao</div>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <button type="submit" class="btn btn-primary">Cadastrar</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>
