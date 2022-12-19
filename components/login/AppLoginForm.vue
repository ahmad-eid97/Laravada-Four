<template>
  <div class="user-area pt-100 pb-70">
    <div class="container">
      <div class="row align-items-center">
        <div class="col-lg-6">
          <div class="user-img">
            <img src="/assets/images/user-img.jpg" alt="Images" />
          </div>
        </div>
        <div class="col-lg-6">
          <div class="user-form">
            <div class="contact-form">
              <h2>Log In</h2>
              <form>
                <div class="row">
                  <div class="col-lg-12">
                    <div class="form-group">
                      <input
                        type="email"
                        class="form-control"
                        :class="
                          (emptyError && !email) || !validEmail
                            ? 'errorInput'
                            : ''
                        "
                        data-error="Please enter your Username or Email"
                        placeholder="Your Email"
                        v-model="email"
                        @change="typingEmail"
                      />
                      <span v-if="emptyError && !email" class="errorHint"
                        >Field is required</span
                      >
                      <span v-if="!validEmail && email" class="errorHint"
                        >Email is invalid</span
                      >
                    </div>
                  </div>
                  <div class="col-12">
                    <div class="form-group">
                      <input
                        class="form-control"
                        :class="emptyError && !password ? 'errorInput' : ''"
                        type="password"
                        name="password"
                        placeholder="Password"
                        v-model="password"
                      />
                      <span v-if="emptyError && !password" class="errorHint"
                        >Field is required</span
                      >
                    </div>
                  </div>
                  <div class="col-lg-12 form-condition">
                    <div class="agree-label">
                      <input type="checkbox" id="chb1" />
                      <label for="chb1">
                        Remember Me
                        <router-link to="forget" class="forget"
                          >Forgot My Password?</router-link
                        >
                      </label>
                    </div>
                  </div>
                  <div class="col-lg-12">
                    <button
                      type="button"
                      class="default-btn btn-bg-two"
                      @click="login"
                    >
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
import * as EmailValidator from "email-validator";

export default {
  name: "AppLoginForm",
  data() {
    return {
      email: "",
      password: "",
      validEmail: true,
      emptyError: false,
    };
  },
  methods: {
    typingEmail() {
      if (EmailValidator.validate(this.email)) {
        this.validEmail = true;
      }
    },
    async login() {
      const data = {
        email: this.email,
        password: this.password,
      };

      if (!this.email || !this.password) {
        this.emptyError = true;
        return this.$toast.error("Please fill all fields!");
      }

      if (!EmailValidator.validate(this.email)) {
        this.validEmail = false;
        return this.$toast.error("Email is invalid!");
      }

      const response = await this.$axios.post("/users/auth/login", data);

      if (!response.data.success) {
        return this.$toast.error(response.data.message);
      }

      this.$store.commit("setUserData", response.data.data.user);

      this.$cookies.set("cms-auth", response.data.data.token, {
        path: "/",
        maxAge: 60 * 60 * 24 * 7,
      });

      this.$cookies.set("cms-user", JSON.stringify(response.data.data.user), {
        path: "/",
        maxAge: 60 * 60 * 24 * 7,
      });

      this.$router.push(this.localePath("/"));
    },
  },
};
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
.errorHint {
  color: #ff7675;
}
.errorInput {
  border-color: #ff7675 !important;
}
</style>
