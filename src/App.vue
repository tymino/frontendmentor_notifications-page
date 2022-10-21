<template>
  <div class="app__header">
    <div class="app__notification-wrapper">
      <div class="app__notification-name">notifications</div>
      <div class="app__notification-name">{{ updateNotificationsCounter }}</div>
    </div>
    <div class="app__button-all-mark">mark all as read</div>
  </div>

  <Card
    v-for="notification in notifications"
    :key="notification.id"
    :data-id="notification.id"
    :cardData="notification"
    @click.once="!notification.hasRead && markAsReadNotify(notification.id)"
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
          hasRead: false,
        },
        {
          id: 2,
          user: 'Angela Gray',
          userAvatar: 'avatar-angela-gray.webp',
          actionType: 'followed',
          actionText: 'followed you',
          actionData: '',
          time: '5m ago',
          hasRead: false,
        },
        {
          id: 3,
          user: 'Jacob Thompson',
          userAvatar: 'avatar-jacob-thompson.webp',
          actionType: 'joined',
          actionText: 'has joined your group',
          actionData: 'Chess Club',
          time: '1 day ago',
          hasRead: false,
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
          hasRead: true,
        },
        {
          id: 5,
          user: 'Kimberly Smith',
          userAvatar: 'avatar-kimberly-smith.webp',
          actionType: 'commented',
          actionText: 'commented on your picture',
          actionData: 'image-chess.webp',
          time: '1 week ago',
          hasRead: true,
        },
        {
          id: 6,
          user: 'Nathan Peterson',
          userAvatar: 'avatar-nathan-peterson.webp',
          actionType: 'reacted',
          actionText: 'reacted to your recent post',
          actionData: '5 end-game strategies to increase your win rate',
          time: '2 weeks ago',
          hasRead: true,
        },
        {
          id: 7,
          user: 'Anna Kim',
          userAvatar: 'avatar-anna-kim.webp',
          actionType: 'lefted',
          actionText: 'left the group',
          actionData: 'Chess Club',
          time: '2 weeks ago',
          hasRead: true,
        },
      ],
    };
  },
  methods: {
    markAsReadNotify(id) {
      this.notifications = this.notifications.map((n) =>
        n.id === id ? { ...n, hasRead: true } : n
      );
    },
  },
  computed: {
    updateNotificationsCounter() {
      return this.notifications.filter((n) => !n.hasRead).length || '';
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
  margin: 60px 20px 20px 20px;
}
</style>
