<template>
  <div id="app">
    @{{ user.username }} - {{ fullName }} <strong>Followers: </strong>
    {{ followers }}
    <button type="button" v-if="!following" @click="followUser">Follow</button>
    <button type="button" v-if="following" @click="unFollowUser">
      UnFollow
    </button>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      followers: 0,
      following: false,
      user: {
        id: 1,
        username: "iAmShaan",
        firstName: "Shantanu",
        lastName: "Dutta",
        email: "shantanudutta1994@gmail.com",
        isAdmin: true,
      },
    };
  },
  watch: {
    followers(newFollowersCount, oldFollowersCount) {
      const gainedOrLost =
        oldFollowersCount < newFollowersCount ? "gained" : "lost";
      console.info(`${this.user.username} has ${gainedOrLost} a follower!`);
    },
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`;
    },
  },
  methods: {
    followUser() {
      if (this.following) {
        return;
      }
      this.followers++;
      this.following = true;
    },
    unFollowUser() {
      if (!this.following) {
        return;
      }
      this.followers--;
      this.following = false;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
