<template>
  <a :href="url" target="_blank" class="resource-item">
    <img v-if="icon" :src="icon" alt="" class="icon" />
    <div v-else class="icon icon--placeholder">
      {{ firstLetter | name }}
    </div>
    <div class="text">
      <h2 class="title">
        {{ name }}
      </h2>
      <p class="description">
        {{ description }}
      </p>
    </div>
  </a>
</template>

<script>
export default {
  name: 'ResourceItem',
  filters: {
    firstLetter(value) {
      if (!value) return ''
      value = value.toString()
      return value.charAt(0)
    }
  },
  props: {
    url: {
      type: String,
      required: true
    },
    name: {
      type: String,
      required: true
    },
    description: {
      type: String,
      default: ''
    },
    icon: {
      type: String,
      default: ''
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/variables';

.resource-item {
  display: flex;
  text-decoration: none;
  padding: 16px 0;
  border-bottom: 1px solid $medium-grey-color;
  transform: translateX(0) translateY(0) translateZ(0);
  transition: all 0.4s ease;
  align-items: center;

  &:hover {
    transform: translateX(5px) translateY(0) translateZ(0);
  }

  &:last-of-type {
    border: none;
  }
}

.title {
  margin-top: 4px;
  margin-bottom: 8px;
  color: $text-color;
  font-family: $primary-font-family;
}

.description {
  margin-top: 0;
  margin-bottom: 8px;
  color: $grey-color;
}

.icon {
  height: 140px;
  width: 140px;
  min-height: 140px;
  min-width: 140px;
  object-fit: contain;
  margin-right: 16px;
  background-color: $light-grey-color;
  border-radius: 3px;
  padding: 16px;

  @media (max-width: 720px) {
    height: 65px;
    width: 65px;
    min-height: 65px;
    min-width: 65px;
    padding: 4px;
  }

  &--placeholder {
    display: flex;
    align-items: center;
    justify-content: center;
    color: $grey-color;
    font-weight: 900;
  }
}
</style>
