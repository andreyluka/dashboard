<script>
export default {
  name: 'appCard',
  props: {
    person: Object
  }
}
</script>

<template>
  <div class="card">
    <div class="card__person">
      <div class="card__photo">
        <img :src="person.Photo" alt="person's photo" class="card__img">
      </div>
      <div class="card__container">
        <h2 class="card__name">{{ person.Name }}</h2>
        <h3 class="card__occupation">{{ person.Title }}</h3>
        <ul class="card__tags">
          <li class="card__tag"
            v-for="(tag, i) in person.Tags"
            :key="i"
            :style="{backgroundColor: `#${tag.Color}`}"
          >{{ tag.Name }}</li>
        </ul>
      </div>
    </div>
    <div class="card__desc">
      <div class="card__container">
        <div class="card__index card__profit">
          <div class="card__index-sign">
            <div class="card__index-name">Profit</div>
            <div class="card__index-count">+ ${{ person.Profit[0].Amount }}</div>
          </div>
          <div class="card__index-graph">
            <div class="card__index-filling"
              :style="{
                backgroundColor: `#${person.Profit[0].Color}`, 
                width: (person.Profit[0].Amount/10)+'%'
              }"
            ></div>
          </div>
        </div>
        <div class="card__index card__attention">
          <div class="card__index-sign">
            <div class="card__index-name">Attention</div>
            <div class="card__index-count">48 h</div>
          </div>
          <ul class="card__index-graph">
            <li 
              class="card__index-filling"
              v-for="fill in person.Attention"
              :key="fill.color"
              :style="{
                backgroundColor: `#${fill.Color}`, 
                width: fill.Amount + '%'
              }"
            ></li>
          </ul>
        </div>
        <div class="card__diagram">
          <ul class="card__rates">
            <li class="card__rate card__rate-1">
              <div class="card__rate-count">15%</div>
              <div class="card__rate-graph">
                <div class="card__rate-filling"></div>
              </div>
            </li>
            <li class="card__rate card__rate-2">
              <div class="card__rate-count">12%</div>
              <div class="card__rate-graph">
                <div class="card__rate-filling"></div>
              </div>
            </li>
            <li class="card__rate card__rate-3">
              <div class="card__rate-count">35%</div>
              <div class="card__rate-graph">
                <div class="card__rate-filling"></div>
              </div>
            </li>
            <li class="card__rate card__rate-4">
              <div class="card__rate-count">38%</div>
              <div class="card__rate-graph">
                <div class="card__rate-filling"></div>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.card {
  background-color: white;
  border-radius: rem(14);
  overflow: hidden;
  display: grid;
  grid-template-rows: 1fr minmax(60px, auto);
  grid-auto-columns: 1fr;
  height: 100%;
  position: relative;
  padding-bottom: rem(32);
}

.card__person {
  margin-bottom: rem(14);
}

.card__container {
  padding: 0 rem(15);
}

.card__photo {
  border-radius: rem(14);
  overflow: hidden;
  height: 180px;
  margin-bottom: rem(5);
}

.card__img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.card__name {
  font-weight: bolder;
}

.card__occupation {
  padding-bottom: rem(5);
  border-bottom: 2px solid $color-gray-light;
}

.card__tags {
  position: absolute;
  top: 10px;
  right: 0;
  transform: translateX(50%);
  color: white;
}

.card__tag {
  font-size: 15px;
  padding: 2px 10px 0;
  border-radius: 6px;
  margin-bottom: 3px;
  cursor: pointer;
  transition: .3s;

  &:hover {
    transform: translateX(-50%);
  }
}

.card__index-sign {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.card__index-count {
  font-weight: 500;
}

.card__index {
  margin-bottom: rem(10);
}

.card__index-graph {
  height: rem(16);
  background-color: $color-gray-light;
  border-radius: 6px;
  display: flex;
  flex-direction: row-reverse;
  justify-content: flex-end;
  overflow: hidden;
}

.card__index-filling {
  border-radius: 6px;
  position: relative;
  animation: load .8s cubic-bezier(.81,.71,.82,1.56);

  &::before {
    content: '';
    display: block;
    width: 10px;
    height: rem(16);
    position: absolute;
    top: 0;
    left: -5px;
    background-color: inherit;
  }
}

.card__attention {
  margin-bottom: rem(22);
}

.card__rates {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: rem(7);
}

.card__rate {
  height: rem(40);
  display: flex;
  align-items: center;
  position: relative;

  .card__rate-filling {
    content: '';
    position: absolute;
    top: 0;
    height: 100%;
    border-radius: 8px;
    animation: load .8s cubic-bezier(.81,.71,.82,1.56);
  }
  
  &:nth-child(1) {
    .card__rate-filling {
      right: 0;
      width: calc(15/50) * 100%;
      background-color: $color-percent-red;
    }
  }
  
  &:nth-child(2) {
    text-align: right;

    .card__rate-filling {
      left: 0;
      width: calc(12/50) * 100%;
      background-color: $color-percent-orange;
    }
  }

  &:nth-child(3) {
    .card__rate-filling {
      right: 0;
      width: calc(35/50) * 100%;
      background-color: $color-percent-blue;
    }
  }

  &:nth-child(4) {
    text-align: right;

    .card__rate-filling {
      left: 0;
      width: calc(38/50) * 100%;
      background-color: $color-percent-green;
    }
  }
}

.card__rate-count {
  font-weight: 500;
  z-index: 10;
  width: 100%;
}

@keyframes load {
  0% { width: 0; }
  100% { width: var(('person.Profit[0].Amount'/10)+'%'); }
}
</style>