<template>
    <div class="user-area pt-100 pb-70">
        <div class="container">
            <div class="row align-items-center">
                <div class="col-lg-6">
                    <div class="user-img">
                        <img src="/assets/images/user-img.jpg" alt="Images">
                    </div>
                </div>
                <div class="col-lg-6">
                    <div class="user-form">
                        <div class="contact-form">
                            <h2>Log In</h2>
                            <form>
                                <div class="row">
                                    <div class="col-lg-12 ">
                                        <div class="form-group">
                                            <input type="text" class="form-control" required="" data-error="Please enter your Username or Email" placeholder="Username or Email" v-model="email">
                                        </div>
                                    </div>
                                    <div class="col-12">
                                        <div class="form-group">
                                            <input class="form-control" type="password" name="password" placeholder="Password" v-model="password">
                                        </div>
                                    </div>
                                    <div class="col-lg-12 form-condition">
                                        <div class="agree-label">
                                            <input type="checkbox" id="chb1">
                                            <label for="chb1">
                                            Remember Me 
                                                <router-link to="forget" class="forget">Forgot My Password?</router-link>
                                            </label>
                                        </div>
                                    </div>
                                    <div class="col-lg-12 "> 
                                        <button type="button" class="default-btn btn-bg-two" @click="login">
                                            Log In Now
                                        </button>
                                    </div>
                                    <div class="col-12">
                                        <p class="account-desc">
                                            Not a Member?
                                            <router-link to="register">Register Now</router-link>
                                        </p>
                                    </div>
                                </div>
                            </form>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'AppLoginForm',
    data() {
        return {
            email: '',
            password: ''
        }
    },
    methods: {
        async login () {
            const data = {
                email: this.email,
                password: this.password
            }
            const response = await this.$axios.post('/api/users/auth/login', data).catch(err => console.log(err));

            if (!response) return;
        }
    }
}
</script>

<style>
.user-area h2 {
  color: #1f365c;
  margin-bottom: 30px;
  font-weight: 700;
  font-size: 26px;
  line-height: 1;
}
.user-form .contact-form .agree-label .forget {
  position: absolute;
  right: 0;
}
</style>