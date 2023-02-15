<template>
    <div class="block-statistics">
        <h2>Статистика:</h2>
        <div>
            <h4>Итоговый доход: {{ allFinance }}</h4>
        </div>
        <div>
            <h4>Итоговый расход: {{ allExpenses }}</h4>
            
        </div>
        <div>
            <h4>Расходы по категориям:</h4>
            <p>Еда: {{ foodExpenses }}</p>
            <p>Одежда: {{ clothExpenses }}</p>
            <p>Развлечение: {{ entertainmentExpenses }}</p>
            <p>Техника: {{ techniqueExpenses }}</p>
            <p>Другое: {{ otherExpenses }}</p>
        </div>
        <div>
            <h4>Самые большие расходы за последний месяц: {{ bigExpenses }}</h4>
            
        </div>
       
    </div>
</template>


<script>
export default {
    data(){
        return{
        expensesArr: JSON.parse(localStorage.getItem("expenses")),
        financeArr: JSON.parse(localStorage.getItem("finance")),
        resultAllFinance: 0,
        resultAllExpenses: 0,
        bigSumma: 0,
        }
    }, 
    methods:{
        fun(){
            console.log(this.expensesArr);
        }
    },

    computed:{
        allFinance(){
            this.resultAllFinance = this.financeArr.map(item => item.summa).reduce((prev, curr) => prev + curr, 0)
            return this.resultAllFinance
        },
        allExpenses(){
            this.resultAllExpenses = this.expensesArr.map(item => item.summa).reduce((prev, curr) => prev + curr, 0)
            return this.resultAllExpenses
        },
        bigExpenses(){
            this.expensesArr.forEach(item => { this.bigSumma < item.summa ? this.bigSumma = item.summa : item});
            let bigSummaProd = this.expensesArr.find(item => item.summa == this.bigSumma)
            return ( `${bigSummaProd.comment} - ${bigSummaProd.summa}`)
        },
        foodExpenses(){
            let food = this.expensesArr.filter(item => item.category == "еда" )
            let res = food.map(item => item.summa).reduce((prev, curr) => prev + curr, 0)
            return res
           
        },
        clothExpenses(){
            let cloth = this.expensesArr.filter(item => item.category == "одежда" )
            let res = cloth.map(item => item.summa).reduce((prev, curr) => prev + curr, 0)
            return res
           
        },
        entertainmentExpenses(){
            let entertainment = this.expensesArr.filter(item => item.category == "развлечение" )
            let res = entertainment.map(item => item.summa).reduce((prev, curr) => prev + curr, 0)
            return res
           
        },
        techniqueExpenses(){
            let technique = this.expensesArr.filter(item => item.category == "техника" )
            let res = technique.map(item => item.summa).reduce((prev, curr) => prev + curr, 0)
            return res
           
        },
        otherExpenses(){
            let other = this.expensesArr.filter(item => item.category == "другое" )
            let res = other.map(item => item.summa).reduce((prev, curr) => prev + curr, 0)
            return res
           
        },
    },
    
    
}
</script>

<style>

</style>