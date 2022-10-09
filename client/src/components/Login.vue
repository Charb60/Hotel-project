<template>
    <div>

        <body>
            <section class="login">

                <div class="left">
                    <div class="contact">
                        <form v-on:submit.prevent="onLogin">
                            <h3><b>เข้าสู่ระบบ</b></h3>
                            <input type="text" v-model="email" placeholder="USERNAME">
                            <input type="password" v-model="password" placeholder="PASSWORD">
                            <p></p>
                            <div class="top_link"><a href="http://localhost:8080/user/create/"><i
                                        class='fa fa-plus-square-o'>สร้างผู้ใช้งาน</i></a></div>
                            <br>
                            <center>
                                <dev class="error" v-if="error">{{error}}</dev>
                            </center>
                            <button class="submit">เข้าสู่ระบบ</button>
                        </form>
                    </div>
                </div>

            </section>
        </body>




    </div>
</template>
<script>
import AuthenService from '@/services/AuthenService'

export default {
    data() {
        return {
            email: '',
            password: ''
        };
    },
    methods: {
        async onLogin() {
            try {
                const response = await AuthenService.login({
                    email: this.email,
                    password: this.password,
                    error: null
                });

                this.$store.dispatch('setToken', response.data.token)
                this.$store.dispatch('setUser', response.data.user)

                this.$router.push({
                    name: 'users'
                })
                console.log(response)

            } catch (error) {
                console.log(error)
                this.error = error.response.data.error
                this.email = ''
                this.password = ''
            }
        },
        navigateTo(route) {
            this.$router.push(route)
        }
    },
}
</script>
<style scoped>
.error {
    color: red;
}

.left .top_link a {
    color: #6d6d6d;
    font-weight: 400;
}

.left .top_link {
    height: 20px;
}

.left .top_link a:hover {
    color: rgb(92, 24, 175);
}

.left .contact {
    display: flex;
    align-items: center;
    justify-content: center;
    align-self: center;
    height: 100%;
    width: 73%;
    margin: auto;
}

.left h3 {
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

.left {
    background: linear-gradient(-45deg, #dcd7e0, #fff);
}

.submit {
    border: none;
    padding: 15px 70px;
    border-radius: 8px;
    display: block;
    margin: auto;
    margin-top: 100px;
    background: #FCE205;
    color: rgb(0, 0, 0);
    font-weight: bold;
    -webkit-box-shadow: 0px 9px 15px -11px rgb(71, 114, 54);
    -moz-box-shadow: 0px 9px 15px -11px rgb(54, 114, 79);
    box-shadow: 0px 9px 15px -11px rgb(54, 114, 72);
}
</style>
