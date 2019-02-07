<template>
  <div class="hello">
    <h1>Selamat Mengerjakan</h1>

    <p :style="'color: red'" v-if="poin < items.length-((items.length*3)/10)">Maaf, Anda Belum Lulus. Silahkan mengikuti SBMPTN</p>
    <p :style="'color: green'" v-else>Selamat, Anda lulus</p>
    <p>{{ 'Poin Anda '+poin}}</p>

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
  name: 'Home',
  data: function(){
    return {
      nama: 'Nafis',
      show: true,
      poin:0,
      jawabanbenar: [],
      items:[
      {
        name:'soal1',
        pertanyaan: 'Aku selalu membersihkan rumah. Siapakah aku ?',
        answer:String,
        check:true,
        pilihan:[
        { pilihan:'Pembantu' },
        { pilihan:'Anak' },
        { pilihan:'Ibu'},
        { pilihan:'Semua jawaban benar' } ],
        jawaban:'Semua jawaban benar'
      },
      {
        pertanyaan: 'Aku adalah anak gembala. Siapakah aku ?',
        name:'soal2',
        check:true,
        answer:String,
        pilihan:[
        { pilihan:'gembala' },
        { pilihan:'anak gembala' },
        { pilihan:'selalu riang' },
        { pilihan:'serta gembira' }
        ],
        jawaban:'anak gembala'
      },
      {
        pertanyaan: 'Presiden kedua Indonesia ?',
        answer:String,
        check:true,
        name:'soal3',
        pilihan:[
        { pilihan:'Jokowi' },
        { pilihan:'Ridwan Kamil' },
        { pilihan:'Ir.Soekarno' },
        { pilihan:'Soeharto' }
        ],
        jawaban:'Soeharto'
      },
      {
        pertanyaan: 'Siapa kita ?',
        answer:String,
        check:true,
        name:'soal3',
        pilihan:[
        { pilihan:'kita siapa ?' },
        { pilihan:'Indonesia' },
        { pilihan:'gatau' },
        { pilihan:'seorang kapiten' }
        ],
        jawaban:'Indonesia'
      },
      {
        pertanyaan: '1 x 1 x 1 x 1 x 1 x 1 ?',
        answer:String,
        check:true,
        name:'soal3',
        pilihan:[
        { pilihan:'1' },
        { pilihan:'-1' },
        { pilihan:'1-' },
        { pilihan:'11' }
        ],
        jawaban:'1'
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
