<script>
import appHeader from './components/appHeader.vue';
import appCard from './components/appCard.vue';

export default {
  components: {
    appHeader,
    appCard
  },
  data() {
    return {
      people: [],
      requestURL: 'https://interview-api-luvkm7etwa-uc.a.run.app/people',
      preloader: false
    }
  },
  methods: {
    async sendRequeste(url, perPage, page) {
      try {
        const urlWithParameters = url + '?pp=' + perPage + '&p=' + page;
        this.preloader = true;
        
        const response = await fetch(urlWithParameters);
        this.people = await response.json();
        
        this.preloader = false;
      } catch (error) {
        alert(error);
      }
    }
  },
  created() {
    this.sendRequeste(this.requestURL);
  }
}
</script>

<template>
  <div class="wrapper">
    <appHeader/>
    <div v-if="preloader" class="preloader">
      <div class="preloader__spinner"></div>
    </div>
    <div class="container">
      <ul class="persons">
        <li class="persons__item"
          v-for="person in people"
          :key="person.Id"
        >
          <appCard :person="person"/>
        </li>
        <li class="persons__item persons__item-button">
          <button type="button" class="persons__button"></button>
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped lang="scss">
.preloader {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background: rgba($color-black, .2);
  z-index: 20;
}

.preloader__spinner {
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;

  &:after {
    content: "⠋";
    display: block;
    font-size: 80px;
    color: brown;
    animation: changeContent .8s linear infinite;
  }
}

@keyframes changeContent {
  10% { content: "⠙"; }
  20% { content: "⠹"; }
  30% { content: "⠸"; }
  40% { content: "⠼"; }
  50% { content: "⠴"; }
  60% { content: "⠦"; }
  70% { content: "⠧"; }
  80% { content: "⠇"; }
  90% { content: "⠏"; }
}


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
  }
  
  @include phones {
    grid-template-columns: 1fr;
    grid-gap: 4.5vw 0;
  }
}

.persons__item {
  width: 100%;
  max-width: 350px;
  margin: 0 auto;
  border-radius: rem(14);
  transition: 0.5s;
  
  &:hover {
    box-shadow: 4.1px 2.9px 20px 0 rgba(0, 0, 0, 0.25);
  }
  
  &:last-child {
    &:hover {
      box-shadow: none;
    }
  }
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
