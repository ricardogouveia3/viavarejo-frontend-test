<template>

<div class="operations">

  <form @submit.prevent="addOperation" class="operations__add">
    <h2 class="operations__add__title">Nova Transação</h2>

    <label for="opType">Tipo da transação</label>
    <select name="opType" id="opType" v-model="opType">
      <option value="-" selected>Compra</option>
      <option value="+">Venda</option>
    </select>

    <label for="prodName">Nome da mercadoria</label>
    <input type="text" name="prodName" id="prodName" placeholder="Input" required v-model="prodName">

    <label for="opValue">Valor</label>
    <input id="opValue" name='opValue' placeholder="R$ 0,00" required v-model="opValue">

    <input type="submit" value="Adicionar transação">
  </form>



  <div class="operations__resume">
    <h2 class="operations__resume__title">Extrato de Transações</h2>
    <div class="operations__resume__header">
      <span class="operations__resume__header__name">Mercadoria</span>
      <span class="operations__resume__header__value">Valor</span>
    </div>
    <ul class="operations__resume__list">
      <li v-for="(data, index) in operations" :key="index">
        <div>
          <span>{{data.type}}</span>
          <span>{{data.name}}</span>
        </div>
        <span>R$ {{data.value.replace(".", ",")}}</span>
      </li>
    </ul>
    <div class="operations__resume__footer">
      <span class="operations__resume__footer__total">Total</span>
      <div class="operations__resume__footer__total-value">
        <span class="operations__resume__footer__total-value__value">R$ {{totalValue()}}</span>
        <span class="operations__resume__footer__total-value__status">[{{totalStatusValue}}]</span>
      </div>
    </div>

  </div>

</div>

</template>

<script>
export default {
  name: 'operations',
  data() {
    return {
      operation: '',
      operations: [],
      totalStatusValue: '',
    }
  },
  methods: {

    totalValue: function(){
      var opTotal = 0.00;
      for (const i of this.operations) {
        if (i.type == "+") { opTotal += Number(i.value); }
        else { opTotal -= Number(i.value); }
      }
      this.totalStatus(opTotal);
      return opTotal;
    },

    totalStatus: function (value) {
      var status = '';
      if (value > 0) { status = 'lucro'; }
      else if (value < 0) { status = 'prejuízo'; }
      else { status = 'neutro'; }

      this.totalStatusValue = status;
    },

    addOperation(){
      this.operations.push({type: this.opType, name: this.prodName, value: this.opValue});
      this.opType = '';
      this.prodName = '';
      this.opValue = '';
    }
  
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.operations {
  display: flex;
  width: 100%;
  flex-wrap: wrap;
}
@media screen and (min-width: 768px) {
  .operations { margin-top: 20px; }
}
form {
  flex-grow: 1;
  display: flex;
  flex-direction: column;
}
@media screen and (min-width: 768px) {
  form {
    padding: 30px;
    border: 1px solid #333;
    border-radius: 5px;
  }
}

label{
  text-align: left;
  font-size: 14px;
  margin-bottom: 10px;
}

select{
  background-image: url('../assets/dropdown-icon.png');
  background-size: 15px 8px;
  background-position: center right 8px;
  background-repeat: no-repeat; 
  cursor: pointer;
}

input,
select {
  border: 0;
  border: 1px solid #999;
  border-radius: 5px;
  padding: 8px 3px;
  appearance: none;
  margin-bottom: 20px;
}

input[type='submit'] {
  cursor: pointer;
  margin-bottom: 0;
  color: #fff;
  background-color: #333;
  border: 0;
  padding: 8px 0;
}

input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

input[type=number] {
  -moz-appearance:textfield;
}

.operations__resume {
  border-top: 1px solid #333;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
  margin-top: 40px;
  padding-top: 15px;
}

@media screen and (min-width: 768px) {
  .operations__resume {
    border-top: 0;
    margin-left: 30px;
    margin-top: 0;
    padding-top: 0;
  }
}
.operations__resume__title,
.operations__add__title {
  font-size: 20px;
  margin-top: 0;
  padding-top: 0;
}

@media screen and (max-width: 768px) {
  .operations__add__title{
    display: none;
  }
}

@media screen and (min-width: 768px) {
  .operations__resume__title{
    padding-top: 30px;
  }
}

.operations__resume__header,
.operations__resume__footer {
  display: flex;
  justify-content: space-between;
  padding: 5px 2ch;
  border-bottom: 1px solid #333;
  font-weight: bold;
}

.operations__resume__footer {
  margin-top: 2px;
  border-top: 1px solid #333;
  border-bottom: 0;
  padding-right: 0;
}

.operations__resume__footer__total-value { text-align: right; }
.operations__resume__footer__total-value__status {
  display: block;
  font-size: 13px;
  font-weight: normal;
  text-transform: uppercase;
}

.operations__resume__list{
  display: flex;
  flex-direction: column;
  list-style: none;
  margin: 0;
  padding: 0;
}
.operations__resume__list li {
  display: flex;
  justify-content: space-between;
  text-align: left;
  padding: 5px 0;
  border-bottom: 1px solid #333;
}
.operations__resume__list li div{
  display: flex;
  max-width: 60%;
}
.operations__resume__list li div span:first-of-type{
  width: 2ch;
  text-align: center;
}
.operations__resume__list li > span{ text-align: right;}

</style>
