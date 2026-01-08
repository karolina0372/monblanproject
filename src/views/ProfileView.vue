<template>
  <div class="profile-page">
    <div class="profile-decor" />
    <div class="profile-view">
      <ProfileHeader />
      <PostList />
    </div>
  </div>
</template>

<script setup>
import ProfileHeader from '@/components/ProfileHeader.vue'
import PostList from '@/components/PostList.vue';
</script>

<style scoped lang="scss">
.profile-page {
  position: relative;
  min-height: 100vh;
  background-color: #fafafa;
}

.profile-decor {
  position: absolute;
  inset: 0;
  pointer-events: none;
  z-index: 0;

  &::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: calc(50% - 28px);
    height: 398px;
    background: top right/100% 398px url('@/assets/images/bg-decor-top.png') no-repeat;
  }

  &::after {
    content: '';
    position: absolute;
    bottom: 41px;
    right: 0;
    width: 100%;
    height: 368px;
    background: url('@/assets/images/bg-decor-bottom.png') no-repeat right bottom;
    background-size: auto 368px;
  }
}

.profile-view {
  position: relative;
  z-index: 1;
  padding-bottom: 200px;
  font-family: 'Roboto', sans-serif;
  display: flex;
  flex-direction: column;
  color: #000;
  position: relative;
}

@include screen(xl) {
  .profile-decor:before {
    background-size: 689px 398px;
  }
}

@include screen(md) {
  .profile-decor:before {
    width: calc(50% - 56px);
    background-size: 100% auto;
  }
}
</style>
