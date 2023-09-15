<script setup>
   
import {ref } from "vue";

const nameuser = ref("");
const tel = ref("");
const table = ref("");
const time = ref("");
const date = ref("");

const getTravelName = (itemName) => {
const travel = travellist.value.find((t) => t.name === itemName);
return travel ? travel.name : "";
};


const bookinglist = ref([
  //"Greedland","Greedland"
]);

function booking(name) {
  const bookingData = {
    name: nameuser.value,
    tel: tel.value,
    table: table.value,
    time: time.value,
    date: date.value,
    itemName: name,
  };
  bookinglist.value.push(bookingData);


  nameuser.value = "";
  tel.value = "";
  table.value = "";
  time.value = "";
  date.value = "";
}
//const travellist=ref(['Iceland','Greedland','fairyland','land of happiness','sky island'])

const travellist=ref([
  {name:'Iceland',price:80 , size: {s:80,m:150,l:200 }},
  {name:'Greedland' ,price:100, size: {s:120,m:150,l:220 }},
  {name:'fairyland',price:120,size: {s:180,m:160,l:230 }},
  {name:'land of happiness',price:130,size: {s:100,m:150,l:250 }},
  {name:'sky island',price:150 ,size: {s:180,m:250,l:300 }},
]);
</script>

<template>
      <div class="container text-center">
        <div class="row">
          <div class="col" >
              <div class="card">
                <img src="src/assets/pic.jpg" class="card-img-top" alt="...">
            <div class="card-body">
                <h5 class="card-title">Iceland</h5>
                        <a class="btn btn-primary" @click="booking('Iceland')">ยืนยันการจอง</a>
      </div>
            </div>
        </div>
          <div class="col">
            <div class="card">
                <img src="src/assets/forrest.jpg" class="card-img-top" alt="...">
              <div class="card-body">
              <h5 class="card-title">Greedland</h5>
                        <a class="btn btn-primary" @click="booking('Greedland')">ยืนยันการจอง</a>

  </div>
</div>
    </div>
  </div>
  
  <div class="row">
    <div class="col">
      <div class="card" >
          <img src="src/assets/farly.jpg" class="card-img-top" alt="...">
  <div class="card-body">
          <h5 class="card-title">fairyland</h5>
          <a class="btn btn-primary" @click="booking('fairyland')">ยืนยันการจอง</a>
</div>
</div>
    </div>
    <div class="col">
      <div class="card">
            <img src="src/assets/happyland.jpg" class="card-img-top" alt="...">
  <div class="card-body">
            <h5 class="card-title">land of happiness</h5>
     <a class="btn btn-primary" @click="booking('land of happiness')">ยืนยันการจอง</a>
  </div>
</div>
    </div>
    <div class="col">
      <div class="card">
            <img src="src/assets/cafe.jpg" class="card-img-top" alt="...">
  <div class="card-body">
    <h5 class="card-title">sky island</h5>   
            <a class="btn btn-primary" @click="booking('sky island')">ยืนยันการจอง</a>
    </div>
        </div>
          </div>
            </div>
                </div>
                     <h1>กรอกข้อมูลที่นี่เสร็จแล้วกดยืนยันว่าอยากได้ร้านไหน</h1>
                    <p class="card-text" >
                          ชื่อผู้จอง <input  typy="text" v-model="nameuser" >
                        </p>
                        <p class="card-text" >
                          จำนวนโต๊ะ <input type="number" v-model="table" >
                        </p>
                        <p class="card-text" >
                          เบอร์ติดต่อ <input  typy="text" v-model="tel" >
                        </p>
                        <p class="card-text" >
                          เวลา <input type="time" v-model="time" >
                        </p>
                        <p class="card-text" >
                        วันที่ <input type="date" v-model="date" >
                        </p>
                      <br>

  <table class="table table-dark table-striped" v-if="bookinglist.length > 0">
  <thead>
        <tr>
        <th scope="col">ลำดับที่</th>
        <th scope="col">ชื่อผู้จอง</th>
        <th scope="col">เบอร์ติดต่อ</th>
        <th scope="col">จำนวนโต๊ะ</th>
        <th scope="col">เวลา</th>
        <th scope="col">วันที่</th>
        <th scope="col">ชื่อร้าน</th>
      </tr>
    </thead>
  <tbody>
    <tr v-for="(item, index) in bookinglist" :key="index">
  <th scope="row">{{ index + 1 }}</th>
  <td scope="row">{{ item.name }}</td>
  <td scope="row">{{ item.tel }}</td>
  <td scope="row">{{ item.table }}</td>
  <td scope="row">{{ item.date }}</td>
  <td scope="row">{{ item.time }}</td>
  <td>{{ getTravelName(item.itemName) }}</td>
</tr>
</tbody>
</table>           
</template>

<style scoped>
</style>
