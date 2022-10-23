<template>
  <div class="card" :class="{ 'card__not-read': !cardData.hasRead }">
    <img
      class="card__avatar"
      :src="`./images/${cardData.userAvatar}`"
      alt=""
      srcset=""
    />
    <div class="card__content">
      <p class="card__info">
        <a class="card__info-user-name" href="">{{ cardData.user }}</a>
        <span class="card__info-action-text">{{ cardData.actionText }}</span>
        <a class="card__info-action-data" v-if="setCardData" href="">
          {{ cardData.actionData }}
        </a>
        <transition name="fade">
          <span class="card__info-action-led" v-if="!cardData.hasRead"></span>
        </transition>
      </p>
      <div class="card__time">{{ cardData.time }}</div>
      <div
        class="card__info-action-message"
        v-if="cardData.actionType === 'message'"
      >
        {{ cardData.actionData }}
      </div>
    </div>
    <img
      class="card__info-action-image"
      v-if="cardData.actionType === 'commented'"
      :src="`./images/${cardData.actionData}`"
      alt="actionData"
      srcset=""
    />
  </div>
</template>

<script>
export default {
  name: 'c-card',
  props: {
    cardData: {
      type: Object,
      default: () => {},
      required: true,
    },
  },
  computed: {
    setCardData() {
      return (
        this.cardData.actionData &&
        this.cardData.actionType !== 'message' &&
        this.cardData.actionType !== 'commented'
      );
    },
  },
};
</script>

<style lang="scss" scoped>
.card {
  display: flex;
  align-items: flex-start;
  width: 100%;
  max-width: 680px;
  padding: 20px;
  margin-bottom: 10px;

  background: none;
  border-radius: var(--border-radius);

  transition: background 0.5s;

  &__not-read {
    background: var(--very-light-grayish-blue);
  }
}

.card__avatar {
  width: 48px;
  height: 48px;
}

.card__content {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  margin-left: 20px;
}

.card__info {
  display: inline-block;

  &-user-name {
    margin-right: 6px;
    color: var(--very-dark-blue);
    font-weight: var(--font-weight-bold);

    &:hover {
      color: var(--color-blue);
    }
  }

  &-action-text {
    margin-right: 6px;
    color: var(--dark-grayish-blue);
  }

  &-action-data {
    margin-right: 6px;
    color: var(--dark-grayish-blue);
    font-weight: var(--font-weight-bold);

    &:hover {
      color: var(--color-blue);
    }
  }

  /* &-action-data {} */

  &-action-led {
    display: inline-block;
    width: 8px;
    height: 8px;
    background: var(--color-red);
    border-radius: 50%;
  }

  &-action-message {
    margin-top: 10px;
    padding: 20px;
    border: 1px solid var(--light-grayish-blue-2);
    border-radius: var(--border-radius);
    color: var(--dark-grayish-blue);

    transition: background 0.4s ease;

    &:hover {
      background: var(--light-grayish-blue-1);
      border: 1px solid var(--light-grayish-blue-1);
    }
  }

  &-action-image {
    width: 48px;
    height: 48px;
    margin-left: auto;
    padding-left: 20px;
    box-sizing: content-box;
  }
}

.card__time {
  margin-top: 6px;
  color: var(--grayish-blue);
}

.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-leave-to {
  opacity: 0;
}

@media (max-width: 600px) {
  .card {
    padding: 14px;
    font-size: 0.9rem;
  }

  .card__avatar {
    width: 40px;
    height: 40px;
  }

  .card__content {
    margin-left: 14px;
  }

  .card__info {
    &-action-image {
      width: 40px;
      height: 40px;
    }
  }
}
</style>
