<template>
    <div>
        <div class="container-scroller">
          <div class="container-fluid page-body-wrapper full-page-wrapper">
            <div class="main-panel">
              <div class="content-wrapper d-flex align-items-center auth">
                <div class="row w-100">
                  <div class="col-lg-4 mx-auto">
                    <div class="auth-form-light text-left p-5">
                      <div class="navbar-brand brand-logo">
                        <img src="../../public/img/logo.svg">
                      </div>
                      <h4>Selamat datang!</h4>
                      <h6 class="font-weight-light">Login untuk mengelola poin pelanggaran siswa.</h6>
                      <form v-on:submit.prevent="Login">
                            <b-form-group
                            id="lbl_email"
                            label="Email"
                            label-for="input_email"
                            >
                            <b-form-input id="input_email" v-model="email" placeholder="Alamat email" trim></b-form-input>
                            </b-form-group>

                            <b-form-group
                            id="lbl_password"
                            label="Password"
                            label-for="input_password"
                            >
                            <b-form-input type="password" id="input_password" v-model="password" placeholder="Kata sandi" trim></b-form-input>
                            </b-form-group>

                            <b-button
                                variant="primary"
                                block
                                type="submit"
                                >Masuk
                            </b-button>
                        </form>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            <!-- content-wrapper ends -->
          </div>
            <b-toast id="loadingToast" title="Processing Data" no-auto-hide>
                <b-spinner label="Spinning" variant="success"></b-spinner>
                <strong class="text-success">Loading...</strong>
            </b-toast>
            <!-- toast untuk tampilan message box -->
            <b-toast id="message" title="Message">
            <strong class="text-success">{{ message }}</strong>
            </b-toast>
        </div>
    </div>
</template>
<script>
export default {
    data() {
      return {
        email: '',
        password: '',
        message: '',
      }
    },
    methods: {
        Login: function(){
            this.$bvToast.show("loadingToast")
            let email = this.email 
            let password = this.password
            this.$store.dispatch('login', { email, password })
            .then((response) => {
                this.message = response.data.message
                this.$bvToast.hide("loadingToast")
                this.$bvToast.show("message")
                this.$router.push('/')
            })
            .catch(err => console.log(err))
        }
    }
}
</script>