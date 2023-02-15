<template>
  <div class="block-expenses">
    <h2>Расходы:</h2>
    <label for="">Сумма:</label>
    <input v-model="summa" type="number" />
    <label for="">Дата:</label>
    <input v-model="date" type="date" />
    <label for="">Сумма:</label>
    <select v-model="category" class="height-20" name="" id="">
      <option
        :value="category"
        v-for="category in categories"
        :key="category.id"
      >
        {{ category.name }}
      </option>
    </select>
    <label for="">Комментарий:</label>
    <input v-model="comment" type="text" />
    <button @click="addExpenses" class="btn">Добавить</button>
  </div>
</template>

<script >
export default {
  data() {
    return {
      summa: 0,
      date: "",
      category: "",
      comment: "",
      newEx: [],
      categories: [
        {
          id: 1,
          name: "еда",
        },
        {
          id: 2,
          name: "одежда",
        },
        {
          id: 3,
          name: "развлечение",
        },
        {
          id: 4,
          name: "техника",
        },
        {
          id: 5,
          name: "другое",
        },
      ],
    };
  },
  methods: {
    addExpenses() {
      let expenses = JSON.parse(localStorage.getItem("expenses"));
      let newData = {
        summa: this.summa,
        data: this.date,
        category: this.category.name,
        comment: this.comment,
      };
      if (expenses == null) {
        this.newEx.push(newData);
        localStorage.setItem("expenses", JSON.stringify(this.newEx));
      } else {
        expenses.push(newData);
        localStorage.setItem("expenses", JSON.stringify(expenses));
      }
      (this.summa = 0),
      (this.date = ""),
      (this.category = ""),
      (this.comment = "");
    },
  },
};
</script>

<style>
.block-expenses {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  border-radius: 10px;
  box-shadow: 0px 0px 5px rgb(122, 63, 4);
}
</style>