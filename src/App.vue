<template>
  <Header
    :counterOfNotification="updateCounterOfNotification"
    @markAll="markAllAsRead"
  />

  <Card
    v-for="notify in notifications"
    :key="notify.id"
    :data-id="notify.id"
    :cardData="notify"
    @click.once="!notify.hasRead && markAsReadNotify(notify.id)"
  />

  <div class="attribution">
    Challenge by
    <a
      href="https://www.frontendmentor.io/challenges/notifications-page-DqK5QAmKbC"
      target="_blank"
      >Frontend Mentor</a
    >. Coded by <a href="https://github.com/tymino">tymino</a>.
  </div>
</template>

<script>
import Card from '@/components/Card.vue';
import Header from '@/components/Header.vue';

export default {
  name: 'App',
  components: {
    Card,
    Header,
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
    markAllAsRead() {
      this.notifications = this.notifications.map((n) => ({
        ...n,
        hasRead: true,
      }));
    },
  },
  computed: {
    updateCounterOfNotification() {
      return this.notifications.filter((n) => !n.hasRead).length;
    },
  },
};
</script>

<style lang="scss">
@font-face {
  font-family: 'PlusJakartaSans';
  src: local('PlusJakartaSans'),
    url(./assets/fonts/PlusJakartaSans-VariableFont_wght.ttf) format('truetype');
}

:root {
  --color-red: hsl(1, 90%, 64%);
  --color-blue: hsl(219, 85%, 26%);
  --color-white: hsl(0, 0%, 100%);
  --very-light-grayish-blue: hsl(210, 60%, 98%);
  --light-grayish-blue-1: hsl(211, 68%, 94%);
  --light-grayish-blue-2: hsl(205, 33%, 90%);
  --grayish-blue: hsl(218, 14%, 63%);
  --dark-grayish-blue: hsl(219, 12%, 42%);
  --very-dark-blue: hsl(224, 21%, 14%);

  --font-size: 16px;
  --font-family: PlusJakartaSans, Helvetica, Arial, sans-serif;
  --font-weight-normal: 500;
  --font-weight-bold: 800;

  --border-radius: 10px;
}

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  text-decoration: none;
}

html {
  font-size: var(--font-size);
  font-family: var(--font-family);
  font-weight: var(--font-weight-normal);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 60px auto;
  background: var(--very-light-grayish-blue);
}

#app {
  padding: 30px;
  background: var(--color-white);
  border-radius: var(--border-radius);
}

.attribution {
  position: absolute;
  top: 2px;
  left: 6px;
  font-size: 0.7rem;
  color: var(--grayish-blue);
  opacity: 0.9;

  a {
    color: var(--dark-grayish-blue);

    &:hover {
      color: var(--grayish-blue);
    }
  }
}

@media (max-width: 600px) {
  body {
    margin: 0px auto;
  }

  #app {
    padding: 14px;
    padding-top: 20px;
  }
}
</style>
