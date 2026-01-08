<template>
  <div class="profile-header">
    <div class="profile-header__icon">
      <img
        src="@/assets/images/profile.png"
        class="profile-header__img"
        alt="Profile Picture"
      >
    </div>
    <div class="profile-header__info">
      <div class="profile-header__title">
        <h1 class="profile-header__name">monblanproject</h1>
        <div class="profile-header__deadline">Start on  17-02-2016</div>
      </div>
      <p class="profile-header__stats">
        <span class="profile-header__stat"><span class="text-bold">870</span> posts</span>
        <span class="profile-header__stat"><span class="text-bold">11,787</span> followers</span>
        <span class="profile-header__stat"><span class="text-bold">112</span> following</span>
      </p>
      <DateFilter />
    </div>
  </div>
</template>

<script setup>
import DateFilter from '@/components/DateFilter.vue'
</script>

<style scoped lang="scss">
.profile-header {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgba(255, 255, 255, .67);
  background-image: linear-gradient(
    to bottom,
    rgba(0, 0, 0, 0.12),
    transparent 24px
  );
  padding: 0 16px;
  height: 172px;
  position: relative;
  filter: drop-shadow(0px 4px 24px rgba(0, 0, 0, .12));

  &__icon {
    width: 138px;
    height: 138px;
  }

  &__info {
    margin-left: 90px;
  }

  &__img {
    width: auto;
    height: 100%;
  }

  &__title {
    display: flex;
    align-items: center;
  }

  &__name {
    font-family: 'Montserrat', sans-serif;
    font-weight: 500;
    font-size: 24px;
    letter-spacing: -0.01em;
    line-height: 29px;
  }

  &__deadline {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-left: 16px;
    font-size: 13px;
    color: #3D8EDA;
    display: flex;
    justify-content: center;
    align-items: center;
    border: 1px solid #3D8EDA;
    border-radius: 2px;
    height: 28px;
    padding: 4px 12px;
  }

  &__stats {
    margin-top: 16px;
    display: flex;
    font-size: 14px;
  }

  &__stat + &__stat {
    margin-left: 24px;
  }
}

.text-bold {
  font-weight: 700;
}

@include screen(md) {
  .profile-header {
    height: auto;
    padding: 20px 16px;

    &__info {
      margin-left: 40px;
    }

    &__title {
      flex-direction: column;
      align-items: flex-start;
    }

    &__deadline {
      margin-left: 0;
      margin-top: 8px;
    }
  }
}

@include screen(sm) {
  .profile-header__info {
    margin-left: 24px;
  }
}
</style>
