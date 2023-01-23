<script>
  export default{
   data(){
    return{
      datasensor:"",
      datasensor2:""
    }
   },
   created(){
   },
   methods:{
    async ubah (){
      const datanodejs = await fetch("http://localhost:82/sensor1")
      const datajson = await datanodejs.json()
      console.log(datajson)
      this.datasensor = datajson.sensor
      console.log(this.datasensor)
    }
   }
  }
</script>

<template>
  <body >
    <div class=" w-1/4 justify-center flex items-center mt-24"> 
    Hello Iam Robot
    <button @click="ubah" class="ml-1 bg-red-700 p-2 rounded-full hover:bg-green-900 font-semibold hover:text-white text-gray-00">Ambil data</button>
    </div>
  <div class="mt-3 flex">
    <table class="border-collapse border border-slate-500 bg-blue-400 uppercase">
      <tr>
        <td class="border p-4 items-center cursor-pointer hover:bg-yellow-500 hover:text-white border-black">Tanggal</td>
        <td class="border p-4 justify-center cursor-pointer hover:bg-yellow-500 hover:text-white border-black"> Lokasi </td>
        <td class="border p-4 justify-center cursor-pointer hover:bg-yellow-500 hover:text-white border-black"> Suhu </td>
        <td class="border p-4 justify-center cursor-pointer hover:bg-yellow-500 hover:text-white border-black"> Kondisi </td>
      </tr>
      <tr v-for ="i in datasensor">
        <td class="border p-4 cursor-pointer hover:bg-slate-500 hover:text-white border-black">{{ i.tanggal }}</td>
        <td class="border p-4 cursor-pointer hover:bg-slate-500 hover:text-white border-black">{{i.lokasi}}</td>
        <td class="border p-4 cursor-pointer hover:bg-slate-500 hover:text-white border-black">{{i.suhu}}</td>
        <td class="border p-4 cursor-pointer hover:bg-slate-500 hover:text-white border-black">{{i.kondisi}}</td>
      </tr>
    </table>
  </div>
  </body>
</template>