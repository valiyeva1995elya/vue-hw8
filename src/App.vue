<template>
  <main>

    <h1>Мои доходы & расходы:</h1>
    <div class="block-main">
      <Finance/>
      <Expenses/>
    </div>
    <Statistics/>
    
  </main>
</template>

<script>
import Expenses from './components/Expenses.vue';
import Statistics from './components/Statistics.vue';
import Finance from './components/Finance.vue';
export default {
  components:{
    Expenses,
    Statistics,
    Finance,
  }

}
</script>

<style>
body{
  background: rgb(249, 243, 231);
  color: rgb(122, 63, 4);
  text-align: center;
}
.btn{
  width: 152px;
  height: 24px;
  margin: 20px;
  background: rgb(122, 63, 4);
  border-radius: 6px;
}
.block-main{
  display: flex;
  justify-content: space-around;
  align-items: flex-start;
}
input {
  width: 150px;
  height: 15px;
  color: rgb(122, 63, 4);
  border-radius: 6px;
  outline: none;
  border: 1px solid rgb(122, 63, 4);
}
select {
  width: 153px;
  height: 23px;
  color: rgb(122, 63, 4);
  border: 1px solid rgb(122, 63, 4);
  border-radius: 6px;
}
.height-20{
    height: 20px;
}

label {
  margin: 10px;
}

</style>