<template>
  <div class="increment-box">
    <button class="sign" @click="decrementNum"><b-icon-bag-dash></b-icon-bag-dash></button>
    <div class="jumlah-angka"><h3>{{ numberString }}</h3></div>
    <button class="sign" @click="incrementNum"><b-icon-bag-plus></b-icon-bag-plus></button>
  </div>
</template>

<script>
// let number = 0;

export default {
  name: 'HelloWorld',
  data(){
    return{
     numberString: 0, 
    }
  },
  methods: {
    incrementNum(){
      this.numberString = this.numberString + 1;
    },

    decrementNum(){
      if(this.numberString > 0){
        this.numberString = this.numberString - 1;
      }
    },
  }
}
</script>

<style>
.increment-box{
  background-color: #fff;
  display: flex;
  justify-content: center;
  height: 60px;
  padding: 10px 10px;
}

.jumlah-angka {
  width: 100px;
  text-align: center;
}

.sign {
  background-color: #6ECB63;
  border: none;
  border-radius: 50%;
  color: white;
  width: 40px;
}

</style>
