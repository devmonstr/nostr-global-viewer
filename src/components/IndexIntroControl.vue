<script setup lang="ts">
import { ref } from "vue";
const props = defineProps({
  isLogined: {
    type: Boolean,
    required: true,
  },
  login: {
    type: Function,
    required: true,
  },
});

// const nip07exists = ref('nostr' in window);
const nip07exists = true;
</script>
<template>
  <div class="p-index-signin" v-if="!props.isLogined" :style="(!nip07exists) ? { display: 'none' } : {}">
    <h2 class="p-index-signin__head">Login for Tweet</h2>
    <div class="p-index-signin__body">
      <input class="p-index-signin__btn" type="button" value="NIP-07 Login" v-on:click="(_$event) => props.login()" />
    </div>
  </div>
  <div class="p-index-intro" v-if="!props.isLogined">
    <h2 class="p-index-intro__head"><span>Welcome</span></h2>
    <p class="p-index-intro__text">How to using Nostr.</p>
    <p class="p-index-intro__text">
      <a href="https://welcome.nostr-jp.org/" rel="noopener" target="_blank" class="p-index-intro__btn">Welcome to
        Nostr</a>
    </p>
    <p class="p-index-intro__text">Please start by reading this introduction.<br />Additionally, if you are interested in more detailed information, exploring from the starting point like</p>
    <p class="p-index-intro__text">
      <a href="https://scrapbox.io/nostr/%E3%81%AF%E3%81%98%E3%82%81%E3%81%A6%E3%81%AENostr%E3%80%90%E3%81%AF%E3%81%98%E3%82%81%E3%81%A6%E3%81%AE%E6%96%B9%E3%81%AF%E3%81%93%E3%81%A1%E3%82%89%E3%80%91"
        rel="noopener" target="_blank" class="p-index-intro__btn">Introduction to Nostr</a>
    </p>
    <p class="p-index-intro__text">might be interesting.</p>
    <h2 class="p-index-intro__head"><span>About this relay</span></h2>
    <p class="p-index-intro__text">For users in Thailand, please configure your Nostr client to use the relay at <code>wss://relay.monstr.ing</code>, as detailed on the back of this page.
    </p>
    <h2 class="p-index-intro__head">Licenses, Source Code, etc.</h2>
    <p class="p-index-intro__text">The source code for this website can be found <br> on <a href="https://github.com/imksoo/nostr-global-viewer"
        class="p-index-intro__text-link" target="_blank">GitHub.</a>
    </p>
    <p class="p-index-intro__text">
      <a href="https://awayuki.github.io/emojis.html" target="_blank" class="p-index-intro__text-link">SUSHIYUKI
        emojis (©awayuki)</a> の絵文字素材や
      <a href="https://soundeffect-lab.info/" target="_blank" class="p-index-intro__text-link">効果音ラボ</a>
      の効果音素材を利用しています。
    </p>
    <p class="p-index-intro__text">なお、私が管理する Nostr リレーの利用規約は<br>
      <a href="https://relay.nostr.wirednet.jp/index.html" class="p-index-intro__text-link"
        target="_blank">relay.nostr.wirednet.jp</a><br>に掲示してあります。
    </p>
  </div>
</template>
<style scoped lang="scss">
.p-index-signin {
  background: rgba(0, 0, 0, 0.6);
  border-radius: 6px;
  padding: 12px;
  display: flex;
  align-items: center;
  gap: 10px;
  margin-top: 1rem;

  &__head {
    color: #ffffff;
    font-size: 14px;
  }

  &__body {
    flex-grow: 1;
    border-left: 1px solid #fff;
    padding-left: 10px;
  }

  &__btn {
    background-color: #fc5fa1;
    color: #ffffff;
    display: block;
    width: 100%;
    box-sizing: border-box;
    padding: 0.5rem 1.4rem;
    border-radius: 2rem;
    transition: all 0.4s;
    border: none;
    line-height: 1;
    cursor: pointer;

    &:hover {
      background-color: #df3d81;
    }
  }
}

.p-index-intro {
  margin-top: 2rem;

  @media screen and (max-width: 880px) {
    margin-top: 0rem;
  }

  &__head {
    font-size: 1.4rem;
    color: gold;
    display: flex;
    gap: 0.4rem;
    align-items: center;
    margin: 2rem 0 1rem 0;

    &::before {
      content: "";
      flex-grow: 1;
      height: 2px;
      background-color: gold;
    }

    &::after {
      content: "";
      flex-grow: 1;
      height: 2px;
      background-color: gold;
    }

    span {
      width: max-content;
      flex-grow: 0;
      flex-shrink: 0;
    }
  }

  &__text {
    color: #ffffff;
    margin: 0;
    line-height: 1.8;
    margin-top: 0.3rem;
  }

  &__text-link {
    color: #fc5fa1;
    font-weight: bold;
  }

  &__text code {
    display: inline-block;
  }

  &__btn {
    background-color: #fc5fa1;
    color: #ffffff;
    display: block;
    padding: 0.5rem 1.4rem;
    border-radius: 2rem;
    transition: all 0.4s;
    line-height: 1;
    margin: 0 auto;
    width: max-content;
  }

  &__btn:hover {
    background-color: #df3d81;
  }
}

@media screen and (max-width: 880px) {
  .p-index-post--signin {
    padding: 12px 0;
  }
}
</style>