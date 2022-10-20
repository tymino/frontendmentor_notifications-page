<template>
  <p>Start</p>

  <Card
    v-for="notification in notifications"
    :key="notification.id"
    :cardData="notification"
  />
</template>

<script>
import Card from '@/components/Card.vue';

export default {
  name: 'App',
  components: {
    Card,
  },
  data() {
    return {
      notifications: [
        {
          id: 1,
          user: 'Mark Webber',
          userAvatar: 'avatar-mark-webber.webp',
          actionType: 'reacted',
          actionText: 'reacted to your recent post',
          actionData: 'My first tournament today!',
          time: '1m ago',
        },
        {
          id: 2,
          user: 'Angela Gray',
          userAvatar: 'avatar-angela-gray.webp',
          actionType: 'followed',
          actionText: 'followed you',
          actionData: '',
          time: '5m ago',
        },
        {
          id: 3,
          user: 'Jacob Thompson',
          userAvatar: 'avatar-jacob-thompson.webp',
          actionType: 'joined',
          actionText: 'has joined your group',
          actionData: 'Chess Club',
          time: '1 day ago',
        },
        {
          id: 4,
          user: 'Rizky Hasanuddin',
          userAvatar: 'avatar-rizky-hasanuddin.webp',
          actionType: 'message',
          actionText: 'sent you a private message',
          actionData:
            "Hello, thanks for setting up the Chess Club. I've been a member for a few weeks now and I'm already having lots of fun and improving my game.",
          time: '5 days ago',
        },
        {
          id: 5,
          user: 'Kimberly Smith',
          userAvatar: 'avatar-kimberly-smith.webp',
          actionType: 'commented',
          actionText: 'commented on your picture',
          actionData: 'image-chess.webp',
          time: '1 week ago',
        },
        {
          id: 6,
          user: 'Nathan Peterson',
          userAvatar: 'avatar-nathan-peterson.webp',
          actionType: 'reacted',
          actionText: 'reacted to your recent post',
          actionData: '5 end-game strategies to increase your win rate',
          time: '2 weeks ago',
        },
        {
          id: 7,
          user: 'Anna Kim',
          userAvatar: 'avatar-anna-kim.webp',
          actionType: 'lefted',
          actionText: 'left the group',
          actionData: 'Chess Club',
          time: '2 weeks ago',
        },
      ],
    };
  },
  methods: {
    getData() {
      console.log('data');
    },
  },
};
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  text-decoration: none;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
