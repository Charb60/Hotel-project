<template>
  <div>
    <b-container class="bv-example-row">
    <b-row class="text-left">
         <b-col cols="10" class="bg3">
          <center>
            <h1><b>รายการที่พักโรงแรม</b></h1>
            <h5>จำนวนรายการที่พักโรงแรม {{ hotels.length }} รายการ</h5>
            <hr>
          </center>
          <div class="d-grid gap-2 col-6 mx-auto">
            <center><b-button variant="success" v-on:click="navigateTo('/hotel/create')"><i class='fa fa-calendar-check-o'>สร้างรายการ</i></b-button></center>
          </div>
          <br>
          <div  class="box3" v-for="hotel in hotels" v-bind:key="hotel.id">
            <h4><b><p>รายการที่พักโรงแรม : {{ hotel.id }}</p></b></h4>
            <p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <b>เลขที่ห้อง : </b>{{ hotel.title }}</p>
            <transition name="fade"> 
              <div class="thumbnail-pic" v-if="hotel.thumbnail != 'null'">
                <p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img :src="BASE_URL+hotel.thumbnail" alt="thumbnail"></p>
              </div>
            </transition>
            <p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<b>รายละเอียดห้องพัก : </b>{{ hotel.content }}</p>
            <p><b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ประเภทที่พัก : </b>{{ hotel.catagori }}</p>
              <p><b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ราคาที่พัก : </b>{{ hotel.price }}</p>
            <hr>
            <p>
              <b-button variant="primary" v-on:click="navigateTo('hotel/'+hotel.id)"> <i class="fa fa-search">ดูรายละเอียด</i></b-button>
              <b-button variant="warning" v-on:click="navigateTo('/hotel/edit/' +hotel.id)"><i class="fa fa-check-square-o">แก้ไขรายการ</i>  </b-button>
              <b-button variant="danger" v-on:click="deleteHotel(hotel)"><i class="fa fa-times">ลบรายการนี้</i>  </b-button>
            </p>
          </div>
        </b-col>
     </b-row>
  </b-container>
  </div>
</template>
<script>
import HotelService from "@/services/HotelsService";
export default {
  data() {
    return {
         BASE_URL: "http://localhost:8081/assets/uploads/",
         hotels: [],
    };
  },
  async created() {
    this.hotels = (await HotelService.index()).data;
  },
  methods: {
    navigateTo(route) {
      this.$router.push(route);
    },
    async deleteHotel(hotel) {
      let result = confirm("คุณแน่ใจนะ ที่จะลบรายการนี้?");
      if (result) {
        try {
          await HotelService.delete(hotel);
          this.refreshData();
        } catch (err) {
          console.log(err);
        }
      }
    },
    async refreshData() {
      this.hotels = (await HotelService.index()).data;
    },
  },
};
</script>
<style scoped>
    .dropbox {
      outline: 2px dashed gray; /* the dash box */
      outline-offset: -10px;
      background: #f5fdaa;
      color: dimgray;
      padding: 10px 10px;
      min-height: 200px; /* minimum height */
      position: relative;
      cursor: pointer;
    }

    .input-file {
        opacity: 0; /* invisible but it's there! */
        width: 100%;
        height: 200px;
        position: absolute;
        cursor: pointer;
    }

    .dropbox:hover {
        background: #fceebe;
    }

    .dropbox p {
        font-size: 1.2em;
        text-align: center;
        padding: 50px 0;
    }

    ul.pictures {
      list-style: none;
      padding: 0;
      margin: 0;
      float: left;
      padding-top: 10px;
      padding-bottom: 10px;
    }
    ul.pictures li {
      float: left;
    }
    ul.pictures li img {
      max-width: 180px;
      margin-right: 20px;
    }
    .clearfix {
      clear: both;
    }
    /* thumbnail */
    .thumbnail-pic img{
      width: 200px;
    }
    input {
      width: 450px;
    }

</style>