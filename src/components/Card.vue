<template>
  <div class="card">
    <img
      class="card__avatar"
      :src="`./images/${cardData.userAvatar}`"
      alt=""
      srcset=""
    />
    <div class="card__content">
      <div class="card__info">
        <a class="card__info-user-name" href="">{{ cardData.user }}</a>
        <div class="card__info-action-text">{{ cardData.actionText }}</div>
        <a class="card__info-action-data" v-if="setCardData" href="">
          {{ cardData.actionData }}
        </a>
        <div class="card__led" v-if="!cardData.hasRead"></div>
      </div>
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
      :src="`./images/${cardData.userAvatar}`"
      alt=""
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
  align-items: center;
  background: rgb(165, 165, 165);
  padding: 10px;
  margin-bottom: 10px;
}
/* .card__avatar {} */
.card__content {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  margin-left: 20px;
}
.card__info {
  display: flex;
  align-items: center;

  &-user-name {
    margin-right: 6px;
    color: red;
  }
  &-action-text {
    margin-right: 6px;
    color: green;
  }
  &-action-data {
    margin-right: 6px;
    color: blue;
  }
}

/* .card__user-name {} */
.card__action-text {
  padding: 0;
  margin: 0 6px;
}
/* .card__action-data {} */
.card__led {
  display: flex;
  width: 8px;
  height: 8px;
  background: red;
  border-radius: 50%;
}
/* .card__time {} */
</style>
