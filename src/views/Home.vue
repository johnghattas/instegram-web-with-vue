<template>
  <v-container pt-0 class="home mt-0" fill-height fluid align-center>
    <v-row class="my-auto pa-0">
      <v-container grid-list-lg class="d-flex justify-center pa-0">
        <v-container class="d-none d-md-flex" id="phoneContainer">
          <v-img src="../assets/phone-animation.png" :eager="false">
            <template placeholder>
              <div v-for="(source, index) in images" :key="index">
                <v-fade-transition>
                  <div class="padding" v-if="index == active">
                    <v-col>
                      <v-img
                        :src="require('@/assets/' + source)"
                        width="235"
                        maxWidth="300"
                        aspect-ratio="0.53"
                        contain
                      >
                      </v-img>
                    </v-col>
                  </div>
                </v-fade-transition>
              </div>
            </template>
          </v-img>
        </v-container>

        <!-- this the secound html -->

        <v-container id="formContainer" align-center>
          <v-col class="ma-0 center ma-20" width="400">
            <!--  -->
            <v-card
              class="white mb-2 d-flex justify-center signUpCotaner"
              width="400"
              outlined
              tile
            >
              <v-col>
                <v-row
                  class="white mb-2 d-flex justify-center pt-2"
                  outlined
                  tile
                >
                  <v-img
                    src="../assets/instegram.png"
                    class="d-flex align-center"
                    max-width="120"
                    centered
                  >
                  </v-img>
                </v-row>

                <div class="dy-2"></div>

                <v-text-field
                  width="200"
                  max-width="200"
                  name="name"
                  label="Phone number, username, or email"
                  filled
                  class="signUpCotaner mb-4"
                  hide-details
                ></v-text-field>
                <div class="dy-2"></div>

                <v-text-field
                  v-model="password"
                  :type="!show3 ? 'password' : 'text'"
                  label="password"
                  color="#8e8e8e"
                  class="signUpCotaner"
                  filled
                  hide-details
                >
                  >
                  <template v-slot:append>
                    <v-fade-transition>
                      <v-icon
                        v-if="password"
                        @click="show3 = !show3"
                        size="16"
                        class="pt-2"
                      >
                        show
                      </v-icon>
                    </v-fade-transition>
                  </template>
                </v-text-field>

                <v-row class="d-flex justify-center mt-5 ma-0">
                  <v-btn
                    block
                    class="py-4"
                    color="primary"
                    @click="loader = 'loading'"
                  >
                    Log In
                  </v-btn>
                </v-row>

                <v-layout
                  row
                  class="ma-0 pt-4"
                  d-flex
                  justify-center
                  align-center
                >
                  <v-divider class="mr-2"></v-divider>
                  <span>OR</span>
                  <v-divider class="ml-2"></v-divider>
                </v-layout>

                <v-row class="ma-0 py-5 d-flex justify-center">
                  <v-icon class="mr-3">mdi-facebook</v-icon>
                  <div>Log in with Facebook</div>
                </v-row>

                <span class="d-flex justify-center mb-2">
                  Forgot passwrod?</span
                >
              </v-col>
            </v-card>

            <!--  -->
            <v-row
              class="white signUpCotaner d-flex justify-center radius ma-0 py-5"
              width="400"
            >
              <div>Don't have an account? <span>Sign up</span></div>
            </v-row>
            <v-col width="400" class="ma-0 pa-0">
              <div class="pt-3"></div>
              <v-row class="d-flex justify-center ma-0 mb-4" width="400"
                >Get the app.</v-row
              >

              <v-layout row class="d-flex justify-center pb-2">
                <div>
                  <v-img
                    class="mr-5 pointer"
                    width="100"
                    draggable="true"
                    @mousedown="googleToggleButton()"
                    @mouseup="googleToggleButton()"
                    @mouseleave="googleButtonSrc = 'google 2.png'"
                    :src="require('@/assets/' + googleButtonSrc)"
                  ></v-img>
                </div>
                <div>
                  <v-img
                    class="pointer"
                    width="100"
                    draggable="true"
                    @mousedown="appleToggleButton"
                    @mouseup="appleToggleButton"
                    @mouseleave="appleButtonSrc = 'apple 2.png'"
                    :src="require('@/assets/' + appleButtonSrc)"
                  ></v-img>
                </div>
              </v-layout>
            </v-col>
          </v-col>
        </v-container>
      </v-container>
    </v-row>
    <v-row class="d-flex flex-column-reverse mb-0 mt-auto">
      <v-footer>
        <v-col>
          <v-row class="d-flex justify-center ma-0 mb-1">
            <div
              class="mr-4 divAbout"
              v-for="(item, index) in arrLine1"
              :key="index"
            >
              {{ item }}
            </div>
          </v-row>

          <v-row class="d-flex justify-center ma-0">
            <div
              class="mr-4 divAbout"
              v-for="(item, index) in arrLine2"
              :key="index"
            >
              {{ item }}
            </div>
          </v-row>
        </v-col>
      </v-footer>
    </v-row>
  </v-container>
</template>

<script>
// @ is an alias to /src

export default {
  name: "Home",
  components: {},
  data() {
    return {
      arrLine1: [
        "About",
        "Blog",
        "Jobs",
        "Help",
        "API",
        "Privacy",
        "Terms",
        "Top Accounts",
        "Hashtags",
        "Locations",
      ],
      arrLine2: [
        "Beauty",
        "Dance & Performance",
        "Fitness",
        "Food & Drink",
        "Home & Garden",
        "Music",
        "Visual Arts",
      ],
      active: 1,

      images: ["img-1.jpg", "img-2.jpg", "img-3.jpg", "img-4.jpg", "img-5.jpg"],
      googleButtonSrc: "google 2.png",
      appleButtonSrc: "apple 2.png",
      show1: false,
      show2: true,
      show3: false,
      show4: false,
      typeField: "password",
      password: "",
      rules: {
        required: (value) => !!value || "Required.",
        min: (v) => v.length >= 8 || "Min 8 characters",
        emailMatch: () => `The email and password you entered don't match`,
      },
    };
  },
  async mounted() {
    setInterval(() => {
      if (this.active + 1 == 5) this.active = -1;
      this.active++;
    }, 10000);
  },
  methods: {
    sleep(ms) {
      return new Promise((resolve) => {
        setTimeout(resolve, ms);
      });
    },
    googleToggleButton() {
      if (this.googleButtonSrc === "google 2.png") {
        this.googleButtonSrc = "google 1.png";
      } else {
        this.googleButtonSrc = "google 2.png";
      }
    },
    appleToggleButton() {
      if (this.appleButtonSrc === "apple 2.png") {
        this.appleButtonSrc = "apple 1.png";
      } else {
        this.appleButtonSrc = "apple 2.png";
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.theme--light.v-footer {
  background-color: #fafafa;

  @media screen and (max-width: 600px) {
    background-color: #fff;
  }
}
span {
  color: #949494;
  font-weight: 600;
  font-size: 12;
}
.home {
  height: 100%;
}
.signUpCotaner {
  border: 1px solid #dbdbdb !important;
}
.center {
  margin: auto 0px;
}
#formContainer {
  width: 400px;
  margin-left: 0px;

  @media screen and (max-width: 960px) {
    margin-left: auto;
    padding: 0;
  }
}

.pointer {
  cursor: pointer;
}
#phoneContainer {
  width: 400px;
  padding: 0;

  margin-right: 0;
}
.v-responsive__content {
  display: flex !important;
}
.padding {
  padding-left: 113px;

  padding-top: 75px;
  position: absolute;
}

.divAbout {
  font-size: 12px;
  line-height: 14px;
}
</style>
