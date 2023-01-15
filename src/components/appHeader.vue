<script>
// defineProps({
//   msg: {
//     type: String,
//     required: true
//   }
// })
</script>

<template>
  <header class="header">
    <div class="header__logo">
      <img alt="logo" class="header__logo-img" src="@/assets/images/logo.svg"/>
    </div>
    <div class="header__controls">
      <button type="button" class="header__btn header__btn-vertical"></button>
      <button type="button" class="header__btn header__btn-horizontal active"></button>
      <button type="button" class="header__btn header__btn-grid"></button>
      <input class="header__search" type="text" name="search" id="search">
      <button type="button" class="header__btn header__btn-filter applied"></button>
      <button type="button" class="header__btn header__btn-sorter applied"></button>
    </div>
    <div class="header__user">
      <div class="header__avatar">
        <img alt="avatar" class="header__avatar-img" src="@/assets/images/houcine.jpg"/>
      </div>
    </div>
  </header>
</template>

<style scoped lang="scss">
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.header__logo {
  width: rem(60);
  height: rem(60);
  background-color: white;
  border-radius: 8px;
  overflow: hidden;
  padding: 3px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.header__controls {
  display: flex;
  align-items: center;
}

.header__btn {
  width: rem(36);
  height: rem(36);
  position: relative;
  margin-right: 10px;
  border: 2px solid $color-background;
  transition: .4s;
  
  &:last-child {
    margin-right: 0;
  }

  &:hover {
    border: 2px solid $color-gray;
    border-radius: 3px;
    background-color: white;
  }

  &::after {
    display: block;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
  
  &-vertical, &-horizontal {
    &::after {
      content: '';
      width: rem(16);
      height: rem(24);
      border: 3px solid $color-black;
      border-radius: 3px;
    }
  }

  &-horizontal {
    &::after {
      width: rem(24);
      height: rem(16);
    }
  }

  &-grid {
    &::after {
      content: url('../assets/images/grid.svg');
      width:rem(32);
      height:rem(32);
    }
  }
  
  &-filter {
    &::after {
      content: url('../assets/images/filter.svg');
      width:rem(22);
      height:rem(22);
    }
  }
  
  &-sorter {
    &::after {
      content: url('../assets/images/sorter.svg');
      width:rem(22);
      height:rem(22);
    }
  }

}
  
.active {
  &::after {
    border-color: $color-blue;
  }
}

.applied {
  &::before {
    content: '';
    display: block;
    width: rem(13);
    height: rem(13);
    border-radius: 50%;
    background-color: $color-red;
    position: absolute;
    top: 0;
    right: 0;
    z-index: 10;
  }
}

.header__search {
  width: rem(250);
  height: rem(28);
  border: 2px solid $color-black;
  border-radius: 10px;
  box-shadow: 0px 6px 5px 0px rgba(34, 60, 80, 0.32);
  outline: none;
  padding: 0 0.4em;
  margin: 0 45px 0 35px;
  position: relative;
  
  &:focus {
    box-shadow: 0px 2px 1px 0px rgba(34, 60, 80, 0.32);
    top: 3px;
  }
}

.header__user {
  position: relative;
  border-radius: 8px;
  overflow: hidden;
  cursor: pointer;
  transition: .3s;
  bottom: 0px;
  
  &:hover {
    box-shadow: 2px 3px 2px 0px rgba(34, 60, 80, 0.32);
    bottom: 2px;
  }
  
  &:active {
    box-shadow: none;
    bottom: 0px;
  }
}

.header__avatar {
  width: rem(60);
  height: rem(60);
}
</style>