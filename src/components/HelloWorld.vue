<template>
  <div class="hello">
    <h1>Selamat Mengerjakan {{nama}}</h1>

    <p :style="'color: red'" v-if="poin < items.length-((items.length*3)/10)">Ayo Lebih Semangat</p>
    <p :style="'color: green'" v-else>Selamat, Anda Pinter</p>
    <h3>{{ 'Poin Anda '+poin}}</h3>

    <div v-for="(item,index) in items" :key="item.pertanyaan" :options="item.pertanyaan">
      <p>{{index+1}}. {{ item.pertanyaan}}</p>
      <div  v-for="pilih in item.pilihan" :key="pilih.pilihan" :options="pilih.pilihan">
        <input type="radio"  :name="'name'+index"
         @click="checkJawaban(index,pilih.pilihan)"
        :value="pilih.pilihan" >{{ pilih.pilihan }}
      </div>
    </div>
  </div>

</template>

<script>
export default {
  name: 'HelloWorld',
  data: function(){
    return {
      nama: 'Athhar',
      show: true,
      poin:0,
      jawabanbenar: [],
      items:[
      {
        name:'soal1',
        pertanyaan: '1 + 1 = ',
        answer:String,
        check:true,
        pilihan:[
        { pilihan:'22' },
        { pilihan:'20' },
        { pilihan:'2'},
        { pilihan:'3' } ],
        jawaban:'2'
      },
      {
        pertanyaan: 'Presiden Pertama Indonesia ?',
        name:'soal2',
        check:true,
        answer:String,
        pilihan:[
        { pilihan:'Sutomo' },
        { pilihan:'Sugriwa' },
        { pilihan:'Suhata' },
        { pilihan:'Soekarno' }
        ],
        jawaban:'Soekarno'
      },
      {
        pertanyaan: 'Presiden kedua Indonesia ?',
        answer:String,
        check:true,
        name:'soal3',
        pilihan:[
        { pilihan:'Sutomo' },
        { pilihan:'Soeharto' },
        { pilihan:'Suhata' },
        { pilihan:'Soekarno' }
        ],
        jawaban:'Soeharto'
      },
      {
        pertanyaan: 'Mengajar pelajaran apa Pa Lukman ?',
        answer:String,
        check:true,
        name:'soal3',
        pilihan:[
        { pilihan:'Matematika' },
        { pilihan:'B.Indonesia' },
        { pilihan:'gatau' },
        { pilihan:'Pbo' }
        ],
        jawaban:'Pbo'
      },
      {
        pertanyaan: 'Siapa walikelas XII RPL 2 ?',
        answer:String,
        check:true,
        name:'soal3',
        pilihan:[
        { pilihan:'Pa Asep' },
        { pilihan:'Bu Dini' },
        { pilihan:'Bu Arne' },
        { pilihan:'Bu Sri' }
        ],
        jawaban:'Bu Dini'
      }
      ]
    }
  },
  methods: {
    hideTitle () {
      this.show = !this.show
    },
    checkJawaban(i,jawab){

      if(this.items[i].jawaban === jawab){
        if(this.jawabanbenar.indexOf(i) == -1){
          this.poin++;
          this.jawabanbenar.push(i);
        }
      }
      if(this.items[i].jawaban !== jawab){
        if(this.jawabanbenar.indexOf(i) != -1){
          this.poin--;
          this.jawabanbenar.splice(this.jawabanbenar.indexOf(i), 1);
        }
      }

        this.items[i].check = false;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
