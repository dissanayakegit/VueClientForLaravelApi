<template>
  <ul>
    <li>
      <router-link :to="{
        name: 'home'
       }">Home</router-link>
    </li>

    <template v-if="authenticated">
      <li>{{user.name}}</li>

      <li>
        <router-link :to="{
        name: 'dashboard'
       }">DashBoard</router-link>
      </li>

      <li>
        <a href="#" @click.prevent="signOut">signout</a>
      </li>
    </template>

    <template v-else>
      <li>
        <router-link :to="{
        name: 'signin'
       }">signin</router-link>
      </li>
    </template>
  </ul>
</template>

<script>
// @ is an alias to /src
import { mapGetters, mapActions } from "vuex";

export default {
  name: "thenavigation",
  components: {},

  computed: {
    ...mapGetters({
      authenticated: "auth/authenticated",
      user: "auth/user"
    })
  },

  methods: {
    ...mapActions({
      signOutAction: "auth/signOut"
    }),
    signOut() {
      this.signOutAction().then(() => {
        this.$router.replace({
          name: "home"
        });
      });
    }
  }
};
</script>
