<template>
  <div class="hero-body" v-on:keyup.enter="sendInstrutions">
    <div class="container has-text-centered">
      <div class="column is-5 is-offset-4">
        <div class="box" v-if="$route.query.id">
          <svg class="svg-circle" viewBox="25 25 50 50" v-if="isLoading">
            <circle cx="50" cy="50" r="20" />
          </svg>
          <div v-else class="notification" v-bind:class="[activated ? 'is-primary' : 'is-danger']">
            <span v-if="activated">PASSWORD ACTIVATED</span>
            <span v-else>PASSWORD NOT ACTIVATED</span>
          </div>
        </div>
        <div class="box" v-else>
          <div class="notification is-info" v-if="message.length === 0">FORGOT EMAIL?</div>
          <div
            class="notification"
            v-bind:class="[error ? 'is-primary' : 'is-danger']"
            v-else
          >INSTRUCTIONS SENT</div>
          <div class="field">
            <p class="control has-icons-left has-icons-right">
              <input class="input is-medium" type="name" v-model="mail" placeholder="Enter email" />
            </p>
          </div>
          <button
            @click="sendInstrutions"
            v-bind:class="{ 'is-loading': isLoading }"
            class="button is-block is-large is-fullwidth"
          >FORGOT?</button>
        </div>
        <p class="has-text-grey">
          <nuxt-link to="/register">Register</nuxt-link>&nbsp;·&nbsp;
          <nuxt-link to="/login">Login</nuxt-link>&nbsp;·&nbsp;
          <nuxt-link to="/forgot-password">Forgot password</nuxt-link>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
</script>

<style>
.column {
  margin-top: 2em;
}
</style>

<script>
import * as _ from "lodash";
export default {
  head() {
    return {
      title: "Forgot password ?"
    };
  },
  async mounted() {
    this.isLoading = this.$route.query ? true : false;
    if (this.$route.query) {
      console.log("activation sent");
    }
  },
  data: function() {
    return {
      mail: null,
      isLoading: false,
      activated: false,
      message: "",
      error: false
    };
  },
  methods: {
    closeNotification() {
      this.$router.replace("/");
    },
    sendInstrutions() {
      console.log("instruction sent");
    }
  }
};
</script>

<style scoped>
.svg-circle {
  width: 3.75em;
  transform-origin: center;
  animation: rotate 2s linear infinite;
}

circle {
  fill: none;
  stroke: #00ddb2;
  stroke-width: 2;
  stroke-dasharray: 1, 200;
  stroke-dashoffset: 0;
  stroke-linecap: round;
  animation: dash 1.5s ease-in-out infinite;
}

@keyframes rotate {
  100% {
    transform: rotate(360deg);
  }
}

@keyframes dash {
  0% {
    stroke-dasharray: 1, 200;
    stroke-dashoffset: 0;
  }
  50% {
    stroke-dasharray: 90, 200;
    stroke-dashoffset: -35px;
  }
  100% {
    stroke-dashoffset: -125px;
  }
}
</style>