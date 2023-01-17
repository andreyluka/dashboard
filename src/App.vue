<script setup>
import appHeader from './components/appHeader.vue'
import appCard from './components/appCard.vue'
</script>

<template>
  <div class="wrapper">
    <appHeader/>
    <div class="container">
      <ul class="persons">
        <li class="persons__item">
          <appCard/>
        </li>
        <li class="persons__item">
          <appCard/>
        </li>
        <li class="persons__item">
          <appCard/>
        </li>
        <li class="persons__item">
          <appCard/>
        </li>
        <li class="persons__item">
          <appCard/>
        </li>
        <li class="persons__item persons__item-button">
          <button type="button" class="persons__button"></button>
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped lang="scss">
.container {
  max-width: 1400px;
  margin: rem(80) auto;
}

.persons {
  display: grid;
  grid-template-columns: repeat(4, 23%);
  justify-content: space-between;
  grid-row-gap: 35px;
  
  @include laptop {
    grid-template-columns: repeat(3, 31%);
    grid-gap: 2.5vw 2.5%;
  }
  
  @include tablets {
    grid-template-columns: 1fr 1fr;
    grid-gap: 2.5vw 2.5%;
  }
  
  @include phones {
    grid-template-columns: 1fr;
    grid-gap: 4.5vw 0;
  }
}

.persons__item {
  max-width: 350px;
  margin: 0 auto;
}

.persons__item-button {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
}

.persons__button {
  width: rem(230);
  height: rem(230);
  border: rem(24) solid white;
  border-radius: 50%;
  transition: .3s;

  &:hover {
    transform: scale(1.1);
  }
  
  &::before, &::after {
    content: '';
    display: block;
    position: absolute;
    background-color: white;
    border-radius: rem(20px);
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
  
  &::before {
    width: rem(116);
    height: rem(24);
  }
  
  &::after {
    width: rem(24);
    height: rem(116);
  }
}
</style>
