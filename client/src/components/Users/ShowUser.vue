<template>
    <div>
        <body>
        <section class="login">
                <div class="left">
                    <div class="contact">
                        <form v-on:submit.prevent = "createUser">
                             <h3>แสดงข้อมูลผู้ใช้งาน</h3>
                                <input type="text" v-model="user.name" placeholder="NAME">
                                <input type="text" v-model="user.lastname" placeholder="LASTNAME">
                                <input type="text" v-model="user.email" placeholder="USERNAME">   
                        </form>
                    
                    </div>
                </div>
        </section>
    </body>
    </div>
</template>
<script>
import UsersService from '@/services/UsersService'
export default {
    data() {
        return {
            user: null,
        };
    },
    async created() {
        try {
            let userId = this.$route.params.userId;
            this.user = (await UsersService.show(userId)).data
        } catch (error) {
            console.log(error);
        }
    },
};
</script>
<style scoped>

.left .top_link a {
    color: #6d6d6d;
    font-weight: 400;
}
.left .top_link{
  height: 20px;
}

.left .top_link a:hover {
  color: rgb(0, 102, 150);
}

.left .contact{
	display: flex;
    align-items: center;
    justify-content: center;
    align-self: center;
    height: 100%;
    width: 73%;
    margin: auto;
}
.left h3{
  text-align: center;
  margin-bottom: 25px;
}
.left input {
    border: none;
    width: 80%;
    margin: 15px 0px;
    border-bottom: 1px solid #3067417d;
    padding: 7px 9px;
    width: 100%;
    overflow: hidden;
    background: transparent;
    font-weight: 600;
    font-size: 14px;
}
.left{
	background: linear-gradient(-45deg, #dcd7e0, #fff);
}
.submit {
    border: none;
    padding: 15px 70px;
    border-radius: 8px;
    display: block;
    margin: auto;
    margin-top: 40px;
    background: #FCE205;
    color: rgb(0, 0, 0);
    font-weight: bold;
    -webkit-box-shadow: 0px 9px 15px -11px rgb(71, 114, 54);
    -moz-box-shadow: 0px 9px 15px -11px rgb(54, 114, 79);
    box-shadow: 0px 9px 15px -11px rgb(54, 114, 72);
}

</style>