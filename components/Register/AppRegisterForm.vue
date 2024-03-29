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
              <h2>Register Now</h2>
              <form>
                <div class="row">
                  <div class="col-lg-12">
                    <div class="form-group">
                      <input
                        type="text"
                        class="form-control"
                        :class="emptyError && !name ? 'errorInput' : ''"
                        required=""
                        data-error="Please enter your Username"
                        placeholder="Enter Your Username"
                        v-model="name"
                      />
                      <span v-if="emptyError && !name" class="errorHint"
                        >Field is required</span
                      >
                    </div>
                  </div>
                  <div class="col-12">
                    <div class="form-group">
                      <input
                        type="email"
                        class="form-control"
                        :class="
                          (emptyError && !email) || !validEmail
                            ? 'errorInput'
                            : ''
                        "
                        required=""
                        data-error="Please enter your Username or Email"
                        placeholder="Enter Your Email"
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

                  <div class="col-lg-12">
                    <button
                      type="button"
                      class="default-btn btn-bg-two"
                      @click="register"
                    >
                      Register Now
                    </button>
                  </div>
                  <div class="col-12">
                    <p class="account-desc">
                      Already have an account?
                      <nuxt-link to="login">Log In</nuxt-link>
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
  name: "AppRegisterForm",
  data() {
    return {
      name: "",
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
    async register() {
      const data = {
        name: this.name,
        email: this.email,
        password: this.password,
      };

      if (!this.name || !this.email || !this.password) {
        this.emptyError = true;
        return this.$toast.error("Please fill all fields!");
      }

      if (!EmailValidator.validate(this.email)) {
        this.validEmail = false;
        return this.$toast.error("Email is invalid!");
      }

      this.$store.state.showLoader = true;

      const response = await this.$axios.post("/users/auth/register", data);

      if (!response.data.success) {
        if (response.data.data) {
          if (response.data.data.name) {
            response.data.data.name.forEach((error) => {
              this.$store.state.showLoader = false;
              return this.$toast.error(error);
            });
          }
          if (response.data.data.email) {
            response.data.data.email.forEach((error) => {
              this.$store.state.showLoader = false;
              return this.$toast.error(error);
            });
          }
          if (response.data.data.password) {
            response.data.data.password.forEach((error) => {
              this.$store.state.showLoader = false;
              return this.$toast.error(error);
            });
          }
        } else {
          this.$store.state.showLoader = false;
          return this.$toast.error(response.data.message);
        }
        return;
      }

      this.$store.commit("setUserData", response.data.data.user);

      this.emptyError = false;
      this.validEmail = true;

      this.$cookies.set("cms-auth", response.data.data.token, {
        path: "/",
        maxAge: 60 * 60 * 24 * 7,
      });

      this.$cookies.set("cms-user", JSON.stringify(response.data.data.user), {
        path: "/",
        maxAge: 60 * 60 * 24 * 7,
      });

      this.$store.state.showLoader = false;

      this.$router.push(this.localePath("/"));
    },
  },
};
</script>

<style>
.contact-form h2 {
  color: #1f365c;
  margin-bottom: 30px;
  font-weight: 700;
  font-size: 26px;
  line-height: 1;
}
.contact-form-area .section-title h2 {
  max-width: 600px;
  color: #212529;
  font-size: 35px;
  font-weight: 800;
  letter-spacing: -1px;
  line-height: 42px;
  text-align: left;
  margin-top: 10px;
  margin-right: auto;
  margin-bottom: 15px;
  margin-left: auto;
  text-align: center;
}

.contact-form-area h2 {
  font-size: 35px;
  font-weight: 600;
  margin-top: 0;
  line-height: 1.2;
  color: #212529;
  margin-bottom: 0;
}
.contact-info::before {
  content: "";
  position: absolute;
  opacity: 0.1;
  z-index: -1;
  top: 0;
  left: 0;
  right: 0;
  width: 100%;
  height: 100%;
  background-image: url(/assets/images/call-shap1.png);
  background-size: cover;
  background-position: center center;
  background-repeat: no-repeat;
}
.contact-form-area .contact-info {
  margin-bottom: 30px;
  background-color: var(--main-color);
  padding: 52px 35px 22px;
  border-radius: 12px;
  position: relative;
  z-index: 1;
}
.contact-form-area .contact-info span {
  color: #fff;
  display: block;
  margin-bottom: 5px;
}
.contact-form-area .contact-info h2 {
  color: #fff;
  font-size: 26px;
  margin-bottom: 15px;
}
.contact-form-area .contact-info p {
  color: #fff;
  margin-bottom: 20px;
}
.contact-form-area .contact-info ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
.contact-form-area .contact-info ul li {
  display: block;
  margin-bottom: 30px;
  padding-left: 60px;
  position: relative;
}
.contact-info ul li .content .icon {
  width: 45px;
  height: 45px;
  line-height: 45px;
  background-color: #fff;
  font-size: 20px;
  color: var(--main-color);
  border-radius: 50px;
  border: 1px solid #fff;
  margin-bottom: 10px;
  text-align: center;
  position: absolute;
  left: 0;
  top: 0;
}
.errorHint {
  color: #ff7675;
}
.errorInput {
  border-color: #ff7675 !important;
}
.contact-info ul li .content h3 {
  font-size: 18px;
  margin-bottom: 10px;
  color: #fff;
  display: block;
}
.contact-form-area .contact-info ul li .content a {
  color: #fff;
  display: block;
  font-weight: 400;
  font-size: 15px;
}
.contact-form .form-group label {
  color: #212529;
  font-size: 15px;
  margin-bottom: 15px;
  font-weight: 500;
}
.contact-form .form-group label span {
  color: var(--main-color);
}
.contact-form .form-group .form-control {
  height: 50px;
  color: #212529;
  border: 1px solid var(--main-color);
  background-color: #fff;
  font-size: 15px;
  padding: 10px 20px;
  width: 100%;
  border-radius: 0;
  font-weight: 500;
}
.contact-form .form-group {
  margin-bottom: 20px;
  position: relative;
}
.contact-form .agree-label {
  margin-bottom: 15px;
  position: relative;
}
.contact-form .agree-label input#chb1 {
  position: absolute;
  top: 5px;
  left: 0;
  width: auto;
  height: auto;
}
.contact-form .agree-label label {
  font-weight: 500;
  color: #252525;
  margin-left: 25px;
}
.contact-form .agree-label label a,
.contact-form a {
  color: var(--main-color);
}

.contact-form .default-btn,
.contact-form .default-btn:hover {
  background-color: var(--main-color);
  border-radius: 25px;
  color: #fff;
  padding: 10px 16px;
  font-weight: bold;
  border: none;
}
button {
  margin-bottom: 10px;
}
</style>
