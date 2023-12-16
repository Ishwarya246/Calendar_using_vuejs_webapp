<template>

  <div class="f1"><h1 id="header">Calendar</h1></div>
  <br>
  <div >
    <section class="f6">
        <h1 style="text-align:right;"> {{ currentMonthName }}</h1>
        <h1 style="text-align: right;"> {{ currentYear }}</h1>
    </section>

    <section class="f2">
      <h2 class="f3" v-for="day in days" :key="day">{{ day }}</h2>
    </section>

    <section class="f5">
      <h2 class="f3" v-for="x in startDayOfMonth() " :key="x"></h2>
      <h2 class="f3" v-for="x in monthlyDays() " :key="x">{{ x }}</h2>
    </section>

    <section class="f6">
        <button class="button" @click="prev">Prev</button>
        <button class="button" @click="next">Next</button>
    </section>

  </div>
  <br>
</template>

<script>
export default {

    data(){
      return {
        days : ["Sun" , "Mon" , "Tues" , "Wed" , "Thur" , "Fri" , "Sat"],
        month : ["January" , "February" , "March" , "April" , "May" , "June" ,"July" , "August" , "September" , "October" , "November" , "December"],
        currentMonth : new Date().getMonth() ,
        currentYear : new Date().getFullYear(),
        daysinmonth : "" ,
        startday : "",
      }
    },

    computed :{
      currentMonthName (){
        return this.month[this.currentMonth] 
      }
    },

    methods :{
      prev(){
        if (this.currentMonth == 0){
          this.currentMonth = 11;
          this.currentYear -- ;
        }
        else{
          this.currentMonth--;
        }
      },
      next(){
        if(this.currentMonth == 11 ){
          this.currentMonth = 0;
          this.currentYear++;
        }
        else{
          this.currentMonth++;
        }
      },
      monthlyDays() {
        this.daysinmonth = new Date(this.currentYear , this.currentMonth + 1, 0) ; 
        return this.daysinmonth.getDate();
      },

      startDayOfMonth() {
        this.startday = new Date(this.currentYear , this.currentMonth , 0) ; 
        return this.startday.getDay() + 1;
      }
    }
}
</script>

<style>
#header {
  text-align: center;
}
.f1{
  padding: 2px ;
  background-color: rgb(3, 244, 236);
}
.f2{

  /* text-align: justify; */
  display: flex;
  flex-direction: row;
  background-color: beige;
  /* justify-content: center; */
}

.f5{
/* text-align: justify; */
display: flex;
flex-direction: row;
background-color: beige;
flex-wrap: wrap;
/* justify-content: center; */
}

.f3{
text-align: center;
width: 14.28%;
}


.f4{
  display: flex;
  justify-content: center;
}

.f6{
  display: flex;
  justify-content: space-between;
  /* text-align: justify; */
}

.button{
  width: 75px;
  text-align: center;
  color: red;
  font-family: cursive;
  height: 30px;
  font-size: larger;
}

</style>