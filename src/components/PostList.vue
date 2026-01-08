<template>
  <div
    class="post-list"
  >
    <div class="post-list__switcher">
      <button
        class="post-switcher post-switcher__tile"
        :class="{'post-switcher__tile_active': viewMode === 'tile'}"
        @click="onSwitch('tile')"
      ></button>
      <button
        class="post-switcher post-switcher__row"
        :class="{'post-switcher__row_active': viewMode === 'row'}"
        @click="onSwitch('row')"
      ></button>
    </div>
    <TransitionGroup
      name="post"
      tag="div"
      class="post-list__content"
      :class="`post-list__content_${viewMode === 'row' ? 'row' : 'tile'}`"
    >
      <PostCard
        v-for="post in postList"
        :key="post.id"
        :data="post"
        :mode="viewMode"
      />
    </TransitionGroup>
    <div class="post-list__btn-container">
      <button class="post-list__btn">Load More</button>
    </div>
  </div>

</template>

<script setup>
import { postList } from '@/assets/data/postList.js'
import PostCard from '@/components/PostCard.vue'
import { ref } from 'vue'

const viewMode = ref('row')

const onSwitch = (mode) => {
  viewMode.value = mode
}
</script>

<style scoped lang="scss">
.post-list {
  display: flex;
  flex-direction: column;
  max-width: 868px;
  padding: 0 16px;
  align-self: center;
  width: 100%;

  &__content {
    display: grid;

    &_tile {
      gap: 16px 8px;
      grid-template-columns: repeat(auto-fill, 203px);
      justify-content: center;
    }
    
    &_row {
      gap: 8px;
      grid-template-columns: 1fr;
    }
  }

  &__switcher {
    display: flex;
    justify-content: flex-end;
    margin-top: 18px;
    margin-bottom: 24px;
  }

  &__btn-container {
    display: flex;
    justify-content: center;
    margin: 16px 0;
  }

  &__btn {
    border-radius: 14px;
    border: 1px solid #929292;
    height: 28px;
    width: 111px;
    background-color: #fafafa;
    color: #929292;
    text-transform: uppercase;
    font-family: 'Roboto', sans-serif;
    font-size: 11px;
    letter-spacing: -0.03em;
    cursor: pointer;

    &:hover {
      background-color: #f0f0f0;
    }

    &:active {
      background-color: #3D8EDA;
      color: #fff;
      border-color: #3D8EDA;
    }
  }
}

.post-switcher {
  height: 22px;
  background: center/contain no-repeat;
  border: none;
  cursor: pointer;
  transition: filter 0.2s ease-in-out;


  &:hover {
    filter: brightness(67%);
  }

  &__tile {
    width: 22px;
    background-image: url('@/assets/images/icon-tile.png');

    &_active {
      background-image: url('@/assets/images/icon-tile-active.png');
      pointer-events: none;
    }
  }

  &__row {
    margin-left: 21px;
    width: 24px;
    background-image: url('@/assets/images/icon-row.png');

    &_active {
      background-image: url('@/assets/images/icon-row-active.png');
      pointer-events: none;
    }
  }
}

.post-move {
  transition: transform 0.3s ease-in-out;
}
</style>
