<template>
  <div class="home-container">
    <div class="menu" @mouseenter="ishover = true" @mouseleave="ishover = false">
      <template v-if="!ishover">
        <ul class="menuber">
          <li class="menu-item"><i class="fas fa-bars fa-2x icon-color fa-fw"></i></li>
          <li class="menu-item"><i class="fas fa-home fa-2x icon-color fa-fw"></i></li>
          <li class="menu-item"><i class="fas fa-paw fa-2x icon-color fa-fw"></i></li>
          <li class="menu-item"><i class="fas fa-bong fa-2x icon-color fa-fw"></i></li>
          <li class="menu-item"><i class="fas fa-dice-d6 fa-2x icon-color fa-fw"></i></li>
        </ul>
      </template>
      <template v-else>
        <ul class="menuber">
          <li class="menu-item">
            <i class="fas fa-times fa-2x icon-color fa-fw"></i>
            <span :class="{ showtitle: ishover }"></span>
          </li>
          <li class="menu-item">
            <nuxt-link to="/">
              <i class="fas fa-home fa-2x icon-color fa-fw"></i>
              <span :class="{ showtitle: ishover }">HOME</span>
            </nuxt-link>
          </li>
          <li class="menu-item">
            <nuxt-link to="/about">
              <i class="fas fa-paw fa-2x icon-color fa-fw"></i>
              <span :class="{ showtitle: ishover }">ABOUT</span>
            </nuxt-link>
          </li>
          <li class="menu-item">
            <nuxt-link to="/made">
              <i class="fas fa-bong fa-2x icon-color fa-fw"></i>
              <span :class="{ showtitle: ishover }">MADE</span>
            </nuxt-link>
          </li>
          <li class="menu-item">
            <i class="fas fa-dice-d6 fa-2x icon-color fa-fw"></i>
            <span :class="{ showtitle: ishover }">NYAAAN</span>
          </li>
        </ul>
      </template>
    </div>
    <div :class="{ bulr: ishover }" class="about-contents">
      <div class="title">
        <p>MADE</p>
      </div>
      <div class="contents">
        <div class="made-item">
          <img src="~/assets/images/made-1.png" alt="pic1">
          <div class="made-contents">
            <p class="made-title">初めて作ったサイト</p>
            <p class="small">TOPの画像はスライドショー</p>
          </div>
        </div>
        <div class="made-item">
          <img src="~/assets/images/made-2.png" alt="pic2">
          <div class="made-contents">
            <p class="made-title">授業で作ったサイト</p>
            <p class="small">ページ遷移時にふわっとするアレを実装！</p>
          </div>
        </div>
        <div class="made-item">
          <img src="~/assets/images/made-3.png" alt="pic3">
          <div class="made-contents">
            <p class="made-title">プロジェクトで作ったサイト</p>
            <p class="small">チーム制作 表示領域に入ったら画像をアニメーションさせた</p>
          </div>
        </div>
      </div>
      <div>
        <Fishes />
      </div>
    </div>
  </div>
</template>
<script>
import Fishes from '~/components/Fishes.vue'
export default {
  head() {
    return {
      link: [
        { rel: 'stylesheet', href: 'https://use.fontawesome.com/releases/v5.8.1/css/all.css' }
      ]
    }
  },
  data: () => ({
    ishover: false
  }),
  components: {
    Fishes
  }
}
</script>
<style lang="scss" scoped>
.home-container {
  font-family: 'M+PLUS+1p';
  display: block;
  background: #fffbf4;
  height: 100%;
  .menu {
    position: fixed;
    z-index: 999;
    width: 52px;
    height: 100vh;
    background-color: #c498a7;
    animation-direction: 3s;
    transition: 0.6s;
    box-shadow: 1px 1px 12px 4px rgba(0,0,0,0.2);
    &:hover {
        width: 200px;
      }
    .menuber {
      padding: 6px;
      list-style-type: none;
      :nth-child(5) {
        position: absolute;
        bottom: 0;
      }
      .menu-item {
        padding-bottom: 2vh;
        font-size: 16px;
        overflow: hidden;
        span {
          padding-left: 10px;
        }
        a {
          text-decoration: none;
        }
      }
    }
  }
}
.bulr {
  background: inherit;
  filter: blur(4px);
  transition: 0.6s;
  }
.icon-color {
  color: #fff;
}
.title {
  position: absolute;
  top: 10vh;
  right: 72%;
  p {
  font-weight: 200;
  font-size: 40px;
  color: #c498a7;
  }
}
.showtitle {
  color: #fff;
  animation-name: fade-in;
  animation-duration: 1s;
  animation-timing-function: ease-out;
  animation-delay: 0s;
  animation-iteration-count: 1;
  animation-direction: normal;
  animation-fill-mode: forwards;
}
@keyframes fade-in {
  0% {opacity: 0; transform: translate3d(0,-20px,0);}
  100% {opacity: 1; transform: translate3d(0,0,0);}
}
.about-contents{
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100vw;
  height: 100vh;
  .contents {
    display: flex;
    flex-wrap: wrap;
    width: 72vw;
    justify-content: space-around;
    align-items: center;
    margin-left: 52px;
    .made-item {
      background: #303755;
      margin: 1%;
      border-radius: 2%;
      text-align: center;
      width: 29%;
      min-width: 320px;
      position: relative;
      img {
        width: 100%;
        height: 100%;
        object-fit: scale-down;
        border-radius: 2% 2% 0 0;
        opacity: 0.6;
        &:hover {
          opacity: 1;
        }
      }
      .made-title {
      color: #fffbf4;
      font-size: 1.1rem;
      font-weight: 300;
      }
      .small {
        color: #c498a7;
        font-size: 0.8rem;
        font-weight: 300;
      }
      .made-contents {
        padding-top: 2%;
      }
    }
  }
}
</style>
