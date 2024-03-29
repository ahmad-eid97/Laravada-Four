<template>
  <header>
    <div class="cart" :class="openCart ? 'opened' : ''">
      <div class="head">
        <i class="fa-regular fa-xmark" @click="openCart = false"></i>
        <button
          @click="goToCheckout"
          :disabled="$store.state.cartItems.length <= 0"
        >
          <i class="fa-regular fa-badge-check"></i> Checkout
        </button>
      </div>
      <cart />
    </div>
    <b-navbar toggleable="lg" class="d-flex justify-content-between">
      <b-navbar-brand :href="localePath('/')">
        <img src="assets/images/logo.png" alt="logoImage" />
      </b-navbar-brand>

      <div class="d-flex align-items-center">
        <div class="smallScr">
          <langSwitch></langSwitch>
          <div class="m-0 cartIcon" @click="openCart = !openCart">
            <span>{{ $store.state.cartItems.length }}</span>
            <i class="fa-regular fa-cart-plus"></i>
          </div>
        </div>

        <b-navbar-toggle target="navbar-toggle-collapse">
          <template #default="{ expanded }">
            <span
              class="menu-trigger"
              :class="expanded ? 'active' : ''"
              id="menu03"
            >
              <span></span>
              <span></span>
              <span></span>
            </span>
          </template>
        </b-navbar-toggle>
      </div>
      <b-collapse
        id="navbar-toggle-collapse"
        class="ml-auto justify-content-end"
        is-nav
      >
        <b-navbar-nav class="align-items-center">
          <b-nav-item
            active-class="active"
            :to="localePath(`/${item.link}`)"
            exact
            v-for="item in $store.state.topMenu"
            :key="item.id"
          >
            <span v-if="!item.child.length">{{ item.label }}</span>

            <b-dropdown
              :text="item.label"
              block
              class="m-2 dropdownBtn"
              v-if="item.child.length"
            >
              <b-dropdown-item
                v-for="child in item.child"
                :key="child.id"
                :to="localePath('/' + child.link)"
                >{{ child.label }}</b-dropdown-item
              >
            </b-dropdown>
          </b-nav-item>
          <b-nav-item v-if="$store.state.user" @click="logout" class="outLarge">
            Logout
          </b-nav-item>
          <b-nav-item class="m-0" @click="$router.push('/qoutation')">
            <nuxt-link :to="localePath('/qoutation')" class="btn"
              >Get qoutation</nuxt-link
            >
          </b-nav-item>
        </b-navbar-nav>

        <div class="largeScr">
          <langSwitch></langSwitch>
          <div class="m-0 cartIcon" @click="openCart = !openCart">
            <span>{{ $store.state.cartItems.length }}</span>
            <i class="fa-regular fa-cart-plus"></i>
          </div>
          <div v-if="$store.state.user" class="logout" @click="logout">
            <i class="fa-regular fa-right-from-bracket"></i>
          </div>
        </div>
      </b-collapse>
    </b-navbar>
  </header>
</template>

<script>
// import DropdownMenu from '@innologica/vue-dropdown-menu'
import cart from "../cart/cart.vue";
import langSwitch from "../langSwitch/langSwitch.vue";
export default {
  name: "AppHeader",
  components: {
    langSwitch,
    cart,
    // DropdownMenu
  },
  data() {
    return {
      side: false,
      openCart: false,
    };
  },
  beforeMount() {
    window.addEventListener("scroll", this.handleScroll);
  },
  mounted() {},
  methods: {
    logout() {
      this.$swal({
        title: "Logout!",
        text: "Are you sure? You want to logout from your account!",
        type: "warning",
        showCancelButton: true,
        confirmButtonColor: "#ff5e57",
        confirmButtonText: "Logout",
      }).then((result) => {
        if (result.value) {
          this.confirmLogout();
        }
      });
    },
    confirmLogout() {
      this.$store.commit("setUserData", null);
      this.$cookies.remove("cms-auth");
      this.$cookies.remove("cms-user");
      this.$router.push(this.localePath("/login"));
    },
    goToCheckout() {
      this.openCart = false;
      this.$router.push("/checkout");
    },
  },
};
</script>
<style lang="scss">
.swal2-container {
  padding: 0 !important;
}
.swal2-shown {
  padding: 0 !important;
}
.swal2-confirm:focus,
.swal2-cancel:focus {
  box-shadow: none !important;
}
.swal2-cancel {
  background: #e5e5e5 !important;
  color: rgb(51, 51, 51) !important;
}
header {
  padding-top: 10px;
  padding-right: 60px;
  padding-bottom: 10px;
  padding-left: 60px;
  min-height: 60px;
  background-color: #fff;
  z-index: 9999;
  @include md {
    padding-right: 10px;
    padding-left: 10px;
  }
}
.cart {
  width: 390px;
  height: 100vh;
  position: fixed;
  top: 0;
  right: 0;
  transform: translateX(390px);
  background-color: #fff;
  z-index: 999999;
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.2);
  .head {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 10px;
    & > i {
      border: 1px solid var(--main-color);
      border-radius: 5px;
      width: 30px;
      height: 30px;
      display: grid;
      place-items: center;
      cursor: pointer;
      font-size: 1rem;
      background-color: var(--main-color);
      color: #fff;
      &:hover {
        color: var(--main-color);
        background: transparent;
      }
    }
    button {
      padding: 5px 30px;
      font-size: 1.2rem;
      background-color: var(--main-color);
      color: #fff;
      border: 1px solid var(--main-color);
      display: flex;
      gap: 5px;
      i {
        font-size: 1.2rem;
      }
      &:disabled {
        opacity: 0.5;
        cursor: not-allowed;
        &:hover {
          background-color: var(--main-color);
          color: #fff;
        }
      }
      &:hover {
        background-color: transparent;
        color: var(--main-color);
      }
    }
  }
  &.opened {
    transform: translateX(0);
  }
  @include xs {
    width: 350px;
  }
}
.cartIcon {
  border: 1px solid var(--main-color);
  border-radius: 5px;
  width: 45px;
  height: 45px;
  display: grid;
  place-items: center;
  cursor: pointer;
  position: relative;
  span {
    position: absolute;
    top: -15px;
    right: -10px;
    width: 30px;
    height: 30px;
    background-color: var(--main-color);
    border-radius: 50%;
    color: #fff;
    display: grid;
    place-content: center;
    font-size: 1.2rem;
    @include sm {
      font-size: 1rem;
    }
  }
  i {
    color: var(--main-color);
  }
  @include sm {
    width: 40px;
    height: 40px;
    margin: 0 10px !important;
  }
  &:hover {
    background-color: var(--main-color);
    i {
      color: #fff;
    }
  }
}
.logout {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background-color: var(--main-color);
  color: #fff;
  display: grid;
  place-items: center;
  font-size: 1.2rem;
  margin: 0 20px;
  cursor: pointer;
  @include md {
    display: none;
  }
}
.outLarge {
  display: none;
  @include md {
    display: inline;
  }
}
.smallScr {
  align-items: center;
  display: none;
  @include md {
    display: flex;
  }
}
.largeScr {
  align-items: center;
  display: flex;
  @include md {
    display: none;
  }
}
.navbar-brand {
  padding-top: 0px !important;
  padding-right: 0px !important;
  margin-right: 25px;
  padding-bottom: 0px !important;
  padding-left: 0px !important;
}
.navbar-brand img {
  max-width: 162px;
  height: auto;
}
.nav-item,
.dropdownBtn {
  position: relative;
  margin: 0 20px;
  justify-content: center;
  transition: all calc(300 * 1ms) cubic-bezier(0.42, 0.01, 0.58, 1);
}
.nav-link {
  font-size: 22px;
  font-weight: 400;
  line-height: 30px;
  color: rgb(97, 106, 125);
}
.active .nav-link,
.nav-link:hover {
  color: var(--main-color) !important;
}

.navbar-toggler,
.navbar-toggler:focus {
  border: none;
  box-shadow: none;
  margin: 0;
}
.menu-trigger,
.menu-trigger span {
  display: inline-block;
  transition: all 0.4s;
  box-sizing: border-box;
}
.menu-trigger {
  position: relative;
  width: 32px;
  height: 25px;
  background: none;
  border: none;
  appearance: none;
  cursor: pointer;
}
.menu-trigger span {
  position: absolute;
  left: 0;
  width: 100%;
  height: 5px;
  background-color: rgb(98, 57, 189);
  border-radius: 4px;
}
.menu-trigger span:nth-of-type(1) {
  top: 0;
}
.menu-trigger span:nth-of-type(2) {
  top: 10px;
}
.menu-trigger span:nth-of-type(3) {
  bottom: 0;
}
#menu03.active {
  transform: rotate(360deg);
}
#menu03.active span:nth-of-type(1) {
  transform: translateY(10px) rotate(-45deg);
}
#menu03.active span:nth-of-type(2) {
  transform: translateY(0) rotate(45deg);
}
#menu03.active span:nth-of-type(3) {
  opacity: 0;
}

nav .btn {
  border-radius: 25px 25px 25px 25px;
  padding-bottom: 13px;
  padding-left: 29px;
  padding-right: 29px;
  padding-top: 13px;
  font-weight: 500;
  justify-content: center;
  letter-spacing: 0.21px;
  font-size: 14px;
  color: rgb(255, 255, 255);
  background-color: #74c5da;
  line-height: 17px;
  min-width: 200px;
  text-transform: uppercase;
  font-family: "Roboto";
  border: none;
}
nav .btn:hover {
  border-radius: 25px 25px 25px 25px;
  padding-bottom: 13px;
  padding-left: 29px;
  padding-right: 29px;
  padding-top: 13px;
  font-weight: 500;
  justify-content: center;
  letter-spacing: 0.21px;
  font-size: 14px;
  color: rgb(255, 255, 255);
  background-color: var(--main-color);
  line-height: 17px;
  min-width: 200px;
  text-transform: uppercase;
  font-family: "Roboto";
  border: none;
}

.nav-item a.active,
.dropdownBtn a.active {
  color: rgb(98, 57, 189) !important;
}

.nav-link.active {
  color: rgb(98, 57, 189) !important;
}

.nav-item {
  @include md {
    &:hover > a,
    &:hover button {
      color: #fff !important;
    }
  }
}

@media screen and (max-width: 991px) {
  .navbar-collapse.show {
    position: absolute;
    left: -60px;
    right: -60px;
    z-index: 9999;
    top: 120%;
  }
  .nav-item,
  .dropdownBtn {
    width: 100%;
    border-bottom: 1px solid #e5e5e5;
    background: #fff;
  }

  .nav-item.active,
  .nav-item:hover {
    background-color: rgb(98, 57, 189);
  }
  .nav-item.active .nav-link,
  .nav-item:hover .nav-link {
    color: #fff;
  }

  .nav-link {
    padding: 16px 30px !important;
    font-weight: 400;
    font-size: 23px;
    text-align: left;
    color: rgb(97, 106, 125);
  }
  .side-bar.opend {
    width: 100%;
  }
}
.dropdownBtn {
  background: transparent !important;
  margin: 0 !important;
  border: none !important;
  button {
    background: none !important;
    padding: 0 !important;
    color: rgb(121, 121, 121) !important;
    text-transform: none !important;
    font-size: 1.4rem !important;
    font-family: unset !important;
    font-weight: 400 !important;
    box-shadow: none !important;
    min-width: unset !important;
  }
  .dropdown-menu {
    top: 40px !important;
  }
}
</style>
