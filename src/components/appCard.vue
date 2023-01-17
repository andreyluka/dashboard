<script>
export default {
  name: 'appCard',
}
</script>

<template>
  <div class="card">
    <div class="card__person">
      <div class="card__photo">
        <img src="@/assets/images/vale.jpg" alt="person's photo" class="card__img">
      </div>
      <div class="card__container">
        <h2 class="card__name">Irina Maslikova</h2>
        <h3 class="card__occupation">Sr Full-stack engineer</h3>
        <ul class="card__tags">
          <li class="card__tag">VueJS</li>
          <li class="card__tag">Golang</li>
          <li class="card__tag">Firebase</li>
          <li class="card__tag">SQL</li>
          <li class="card__tag">ReactJS</li>
        </ul>
      </div>
    </div>
    <div class="card__desc">
      <div class="card__container">
        <div class="card__index card__profit">
          <div class="card__index-sign">
            <div class="card__index-name">Profit</div>
            <div class="card__index-count">+ $257</div>
          </div>
          <div class="card__index-graph">
            <div class="card__index-filling"></div>
          </div>
        </div>
        <div class="card__index card__attention">
          <div class="card__index-sign">
            <div class="card__index-name">Attention</div>
            <div class="card__index-count">48 h</div>
          </div>
          <div class="card__index-graph">
            <div class="card__index-filling card__index-filling-2"></div>
            <div class="card__index-filling card__index-filling-1"></div>
          </div>
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
  right: -13%;
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

  &:nth-child(1) {
    background-color: $color-orange-dark;
  }

  &:nth-child(2) {
    background-color: $color-green-dark;
  }

  &:nth-child(3) {
    background-color: $color-yellow-dark;
  }

  &:nth-child(4) {
    background-color: $color-purple-dark;
  }

  &:nth-child(5) {
    background-color: $color-blue-dark;
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
  border-radius: 6px;
  position: relative;
}

.card__index-filling {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  border-radius: 6px;
}

.card__profit {
  .card__index-graph {
    background-color: $color-gray-light;
  }
  .card__index-filling {
    width: 45%;
    background-color: $color-green-dark;
  }
}

.card__attention {
  margin-bottom: rem(22);

  .card__index-graph {
    background-color: $color-attention-yellow;

    .card__index-filling-2 {
      width: 69%;
      background-color: $color-attention-purple;
    }
    .card__index-filling-1 {
      width: 33%;
      background-color: $color-attention-pink;
    }
  }
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
</style>