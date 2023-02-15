<template>
  <div class="block-finance">
    <h2>Доходы:</h2>
    <label for="">Сумма:</label>
    <input type="number" v-model="summa" />
    <label for="">Дата:</label>
    <input type="date" v-model="date" />
    <label for="">Источник:</label>
    <input type="text" v-model="source" />
    <label for="">Комментарий:</label>
    <input type="text" v-model="comment" />
    <button class="btn" @click="addFinance">Добавить</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      summa: 0,
      date: "",
      source: "",
      comment: "",
      newFin: [],
    };
  },
  methods: {
    addFinance() {
      let finance = JSON.parse(localStorage.getItem("finance"));
      let newData1 = {
        summa: this.summa,
        data: this.date,
        source: this.source,
        comment: this.comment,
      };
      if (finance == null) {
        this.newFin.push(newData1);
        localStorage.setItem("finance", JSON.stringify(this.newFin));
      } else {
        finance.push(newData1);
        localStorage.setItem("finance", JSON.stringify(finance));
      }
      (this.summa = 0),
      (this.date = ""),
      (this.source = ""),
      (this.comment = "");
    },
  },
};
</script>

<style>
.block-finance {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  border-radius: 10px;
  box-shadow: 0px 0px 5px rgb(122, 63, 4);
}
</style>