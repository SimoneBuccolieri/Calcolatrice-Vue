<template>

  <div id="calcolatrice" class=" h-screen container mx-auto py-8 flex flex-col justify-center items-center">
    <h1 class="text-4xl font-bold">Calcolatrice</h1>
    <div class="bg-gray-300 border border-gray-500 rounded p-6">

      <div class="">
        <input class="bg-white m-2 rounded border border-gray-500 mb-16" type="text" v-model="schermo">
      </div>
      <div class="grid grid-cols-4 gap-2">
        <div class="flex flex-col space-y-2">
          <button class="h-[41px] bg-white rounded border border-gray-500 " @click="concatenanumero(1)">1</button>
          <button class="h-[41px] bg-white rounded border border-gray-500 " @click="concatenanumero(4)">4</button>
          <button class="h-[41px] bg-white rounded border border-gray-500 " @click="concatenanumero(7)">7</button>
          <button class="h-[41px] bg-white rounded border border-gray-500 " @click="reset()">clear</button>
        </div>
        <div class="flex flex-col space-y-2">
          <button class="h-[41px] bg-white rounded border border-gray-500  " @click="concatenanumero(2)">2</button>
          <button class="h-[41px] bg-white rounded border border-gray-500 " @click="concatenanumero(5)">5</button>
          <button class="h-[41px] bg-white rounded border border-gray-500 " @click="concatenanumero(8)">8</button>
          <button class="h-[41px] bg-white rounded border border-gray-500 " @click="concatenanumero(0)">0</button>

        </div>
        <div class="flex flex-col  space-y-2">
          <button class="h-[41px] bg-white rounded border border-gray-500 " @click="concatenanumero(3)">3</button>
          <button class="h-[41px] bg-white rounded border border-gray-500 " @click="concatenanumero(6)">6</button>
          <button class="h-[41px] bg-white rounded border border-gray-500 " @click="concatenanumero(9)">9</button>
          <button class="h-[41px] bg-white rounded border border-gray-500 " @click="uguale()">
            <svg fill="#000000" viewBox="-3 0 19 19" xmlns="http://www.w3.org/2000/svg" class="cf-icon-svg"><path d="M.289 6.883a1.03 1.03 0 0 1 1.03-1.03h10.363a1.03 1.03 0 0 1 0 2.059H1.318A1.03 1.03 0 0 1 .29 6.882zm12.422 4.604a1.03 1.03 0 0 1-1.03 1.03H1.319a1.03 1.03 0 1 1 0-2.059h10.364a1.03 1.03 0 0 1 1.029 1.03z"/></svg>
          </button>
        </div>
        <div class="flex flex-col  space-y-2">
          <button class="h-[41px] bg-white rounded border border-gray-500 " @click="somma()">
            <svg fill="#000000" viewBox="0 0 24 24" id="plus" data-name="Flat Color" xmlns="http://www.w3.org/2000/svg" class="icon flat-color"><path id="primary" d="M12,20a1,1,0,0,1-1-1V13H5a1,1,0,0,1,0-2h6V5a1,1,0,0,1,2,0v6h6a1,1,0,0,1,0,2H13v6A1,1,0,0,1,12,20Z" style="fill: rgb(0, 0, 0);"></path></svg>
          </button>
          <button class="h-[41px] bg-white rounded border border-gray-500 " @click="moltiplicazione()">
            <svg fill="#000000" viewBox="-3.5 0 19 19" xmlns="http://www.w3.org/2000/svg" class="cf-icon-svg"><path d="M11.383 13.644A1.03 1.03 0 0 1 9.928 15.1L6 11.172 2.072 15.1a1.03 1.03 0 1 1-1.455-1.456l3.928-3.928L.617 5.79a1.03 1.03 0 1 1 1.455-1.456L6 8.261l3.928-3.928a1.03 1.03 0 0 1 1.455 1.456L7.455 9.716z"/></svg>
          </button>
          <button class="h-[41px] bg-white rounded border border-gray-500 " @click="divisione()">
            <svg viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M5 11C4.44772 11 4 10.5523 4 10C4 9.44772 4.44772 9 5 9H15C15.5523 9 16 9.44772 16 10C16 10.5523 15.5523 11 15 11H5Z" fill="#000000"/>
              <circle cx="10" cy="5.5" r="1.5" fill="#000000"/>
              <circle cx="10" cy="14.5" r="1.5" fill="#000000"/>
            </svg>
          </button>
          <button class="h-[41px] bg-white rounded border border-gray-500 " @click="differenza()">
            <svg fill="#000000" viewBox="0 0 24 24" id="minus" data-name="Flat Color" xmlns="http://www.w3.org/2000/svg" class="icon flat-color"><path id="primary" d="M19,13H5a1,1,0,0,1,0-2H19a1,1,0,0,1,0,2Z" style="fill: rgb(0, 0, 0);"></path></svg>
          </button>
        </div>
      </div>

    </div>

  </div>
</template>

<script>
export default {
  data() {
    return {
      schermo: 0,
      temp:0,
      operator:'0',
      clear:false,
    };
  },
  methods: {
    concatenanumero(num){
      if (this.schermo == 0 || this.clear==true){
        this.schermo = num.toString();
        this.clear=false;
      }
      else
        this.schermo += num.toString();
    },
    somma(){
      if(this.operator!='0' && this.clear==false){
        this.uguale();
      }
      this.clear=true;
      this.operator='som';
      this.temp=this.schermo;


    },
    differenza(){
      if(this.operator!='0' && this.clear==false){
        this.uguale();
      }
      this.clear=true;
      this.operator='dif';
      this.temp=this.schermo;
    },
    moltiplicazione(){
      if(this.operator!='0' && this.clear==false){
        this.uguale();
      }
      this.clear=true;
      this.operator='mol';
      this.temp=this.schermo;
    },
    divisione(){
      if(this.operator!='0' && this.clear==false){
        this.uguale();
      }
      this.clear=true;
      this.operator='div';
      this.temp=this.schermo;
    },
    uguale(){
      switch (this.operator) {
        case 'som':
          this.schermo = parseInt(this.temp) + parseInt(this.schermo);
          break;
        case'dif':
          this.schermo = parseInt(this.temp) - parseInt(this.schermo);
          break;
        case'mol':
          this.schermo = parseInt(this.temp) * parseInt(this.schermo);
          break;
        case'div':
          this.schermo = parseInt(this.temp) / parseInt(this.schermo);
          break;
      }
      this.operator='0';
      this.clear=true;
      },
    reset(){
      this.temp=0;
      this.schermo=0;
      this.operator='0';
      this.clear=false;
    },
  }
};
</script>
<style>

</style>
