<template>
  <div class="user-profile">
    <div class="user-profile__user-panel">
      <h1 class="user-profile__user-name">@{{ user.username }}</h1>
      <div class="user-profile__follower-count">
        <strong>Followers: </strong> {{ followers }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "UserProfile",
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
.user-profile {
  display: grid;
  grid-template-columns: 1fr 3fr;
  width: 100%;
  padding: 50px 5%;
}

.user-profile__user-panel {
  display: flex;
  flex-direction: column;
  margin-right: 50px;
  padding: 20px;
  background-color: white;
  border-radius: 5px;
  border: 1px solid #dfe3e8;
}

h1 {
  margin: 0;
}
</style>