<template>
  <div class="user-profile">
    <div class="user-profile__user-panel">
      <h1 class="user-profile__user-name">@{{ user.username }}</h1>
      <div class="user-profile__admin-badge" v-if="user.isAdmin">Admin</div>
      <div class="user-profile__follower-count">
        <strong>Followers: </strong> {{ followers }}
      </div>
    </div>
    <div class="user-profile__twoots-wrapper">
      <TwootItem
        v-for="twoot in user.twoots"
        :key="twoot.id"
        :username="user.username"
        :twoot="twoot"
        @favourite="toggleFavourite"
      />
    </div>
  </div>
</template>

<script>
import TwootItem from "./TwootItem";
export default {
  name: "UserProfile",
  components: {
    TwootItem,
  },
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
        twoots: [
          {
            id: 1,
            content: "Twooter is amazing!",
          },
          {
            id: 2,
            content: "Keep using Twooter.",
          },
        ],
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
    toggleFavourite(id) {
      console.log(`Favourited tweet #${id}`);
    },
  },
};
</script>

<style>
.user-profile {
  display: grid;
  grid-template-columns: 1fr 3fr;
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

.user-profile__admin-badge {
  background: rebeccapurple;
  color: white;
  border-radius: 5px;
  padding: 2px 10px;
  margin-right: auto;
  font-weight: 600;
  margin-top: 0.5rem;
  margin-bottom: 0.5rem;
}
</style>