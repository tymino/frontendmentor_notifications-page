<template>
  <div class="header">
    <div class="header__notification">
      <div class="header__notification-name">notifications</div>
      <div
        class="header__notification-counter"
        v-if="counterOfNotification > 0"
      >
        {{ counterOfNotification }}
      </div>
    </div>
    <div class="header__button-all-mark" @click="$emit('markAll')">
      mark all as read
    </div>
  </div>
</template>

<script>
export default {
  name: 'c-header',
  props: {
    counterOfNotification: {
      type: Number,
      default: 0,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped>
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 20px;

  &__notification {
    display: flex;
    align-items: flex-end;
    font-weight: var(--font-weight-bold);

    &-name {
      font-size: 1.5rem;
      text-transform: capitalize;
    }
    &-counter {
      margin-left: 14px;
      padding: 4px 14px;
      background: var(--color-blue);
      border-radius: var(--border-radius);
      color: var(--color-white);
      font-size: 1.1rem;
    }
  }

  &__button-all-mark {
    color: var(--dark-grayish-blue);

    &:first-letter {
      text-transform: capitalize;
    }
  }
}
</style>
