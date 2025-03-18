<template>
  <div class="breadcrumbs">
    <ul class="breadcrumbs__list">
      <li
        v-for="(item, index) in breadcrumbs"
        :key="item.text"
        class="breadcrumbs__item"
      >
        <NuxtLink
          :to="item.url"
          class="breadcrumbs__link"
          :class="{
            'breadcrumbs__link--disabled': index == breadcrumbs.length - 1,
          }"
        >{{ item.text }}</NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script setup>
defineProps({
  breadcrumbs: {
    type: Array,
    validator: function (value) {
      return value.every((item) => {
        return typeof item.url === 'string' && typeof item.text === 'string'
      })
    },
    default: () => [],
  },
})
</script>

<style lang="scss" scoped>
.breadcrumbs {
  margin-bottom: 50px;
  &__list {
    width: fit-content;
    display: flex;
    flex-wrap: wrap;
    gap: 6px 12px;
    align-items: center;
  }
  &__item {
    font-size: 16px;
    display: flex;
    gap: 12px;
    &:not(:last-child) {
      &::after {
        content: "";
        display: block;
        height: 2px;
        width: 2px;
        border-radius: 50%;
        //background-color: var(--text-default);
        margin: auto;
      }
    }
  }
  &__link {
    //transition: color var(--time);
    &:hover {
      color: var(--text-accent);
    }
    &--disabled {
      pointer-events: none;
      //color: var(--text-default);
    }
  }
}
@include tablet {
  .breadcrumbs {
    margin-bottom: 30px;
    &__item {
      font-size: 14px;
    }
  }
}
@include mobile {
  .breadcrumbs {
    margin-bottom: 20px;
    &__list {
      gap: 2px 6px;
    }
    &__item {
      font-size: 12px;
      gap: 6px;
    }
  }
}
</style>
