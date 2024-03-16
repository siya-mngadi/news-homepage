<template>
  <div class="row main-section">
    <div class="col-md-8">
      <div class="main-content">
        <div class="main-img">
          <v-img :src="homeIcon" />
        </div>
        <div class="row my-4">
          <div class="col-sm-6">
            <h1>The Bright Future of Web 3.0?</h1>
          </div>
          <div class="col-sm-6">
            <div>
              <span class="text-muted">
                We dive into the next evolution of the web that claims to put the power of the
                platform back into the hands of the people. But is it really fulfilling its promise?
              </span>
            </div>

            <div>
              <v-btn :elevation="0" size="large" class="btn-more my-3"> Read More </v-btn>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="col-md-4">
      <div class="side-section" id="new">
        <h1>New</h1>

        <template v-for="(newItem, index) in news" :key="newItem.title">
          <section class="side-item">
            <h5>{{ newItem.title }}</h5>
            <span>{{ newItem.body }}</span>
          </section>
          <v-divider v-if="index < news.length - 1"></v-divider>
        </template>
      </div>
    </div>
  </div>
  <div class="secondary-section" id="popular">
    <div class="row">
      <template v-for="(item, index) in points" :key="index">
        <div class="col-md-4">
          <v-card :elevation="0">
            <div class="card-content">
              <div class="card-image">
                <v-img :height="125" aspect-ratio="1" :src="item.img" />
              </div>
              <div class="card-info">
                <h4>0{{ index + 1 }}</h4>
                <h5>{{ item.title }}</h5>
                <span class="text-muted">{{ item.body }}</span>
              </div>
            </div>
          </v-card>
        </div>
      </template>
    </div>
  </div>
</template>

<script setup lang="ts">
import { useWindowSize } from '@vueuse/core'
import { computed } from 'vue'
import desktopIcon from '@/assets/images/image-web-3-desktop.jpg'
import mobileIcon from '@/assets/images/image-web-3-mobile.jpg'
import retroPCs from '@/assets/images/image-retro-pcs.jpg'
import keyboard from '@/assets/images/image-top-laptops.jpg'
import games from '@/assets/images/image-gaming-growth.jpg'

const news = [
  { title: 'Hydrogen VS Electric Cars', body: 'Will hydrogen-fueled cars ever catch up to EVs?' },
  {
    title: 'The Downsides of AI Artistry',
    body: 'What are the possible adverse effects of on-demand AI image generation?'
  },
  {
    title: 'Is VC Funding Drying Up?',
    body: 'Private funding by VC firms is down 50% YOY. We take a look at what that means.'
  }
]

const points = [
  {
    title: 'Reviving Retro PCs',
    img: retroPCs,
    body: 'What happens when old PCs are given modern upgrade?'
  },
  {
    title: 'Top 10 Laptops of 2022',
    img: keyboard,
    body: 'Our best picks for various needs and budgets.'
  },
  {
    title: 'The Growth of Gaming',
    img: games,
    body: 'How the pandemic has sparked fresh opportunites.'
  }
]

const mobileWidth = 575

const { width } = useWindowSize()

const homeIcon = computed(() => {
  if (width.value <= mobileWidth) return mobileIcon
  return desktopIcon
})
</script>

<style lang="scss" scoped>
.card-content {
  display: flex;
  flex-wrap: wrap;
}

.card-image {
  height: auto;
  flex: 1;
  padding-bottom: 1rem;
}

.card-info {
  flex: 2;
}

.side-section {
  margin-right: 1rem;
  padding: 20px 18px;
  color: var(--off-white);
  background-color: var(--very-dark-blue);

  h1 {
    color: var(--orange-soft);
  }

  .side-item {
    margin-top: 2rem;
    min-height: 5rem;

    span {
      color: var(--grayish-blue);
      font-size: 13px;
    }
  }
}

.secondary-section {
  margin-top: 2rem;
  h4 {
    color: var(--grayish-blue);
    font-size: xx-large;
  }

  h5 {
    color: var(--very-dark-blue);
    font-weight: bold;
  }
}

.btn-more {
  color: var(--off-white);
  background-color: var(--red-soft);
}
</style>
