<script lang="ts">
import { useI18n } from 'vue-i18n';

import { defineComponent, ref } from 'vue';
import { useTheme } from '/@/composables';

export default defineComponent({
  name: 'Home',
  setup() {
    const { t, availableLocales, locale } = useI18n();

    const toggleLocales = () => {
      const locales = availableLocales;
      locale.value =
        locales[(locales.indexOf(locale.value) + 1) % locales.length];
    };

    const { toggleDark } = useTheme();

    const show = ref(false);

    setTimeout(() => {
      show.value = true;
    }, 1000);

    return { t, show, toggleLocales, toggleDark };
  },
});
</script>
<template>
  <div class="container max-w-3xl mx-auto">
    <div class="h-60 mb-8">
      <transition
        enter-active-class="transition ease-out duration-1000 transform"
        enter-from-class="-translate-x-100 opacity-0"
        enter-to-class="translate-x-0 opacity-100"
        leave-active-class="transition ease-in duration-1000 transform"
        leave-from-class="opacity-100"
        leave-to-class="opacity-0"
      >
        <img
          v-if="show"
          alt="TSIT logo"
          class="w-52 mx-auto mb-12"
          :src="'tsit_logo.svg'"
        />
      </transition>
      <p class="text-center text-2xl">
        Kickstart your next IT Solution development
      </p>
    </div>

    <HelloWorld :msg="t('hello') + ' 👋 ' + t('welcome')" />

    <footer class="text-center">
      <ul class="flex justify-between w-1/3 mx-auto mb-8">
        <li class="cursor-pointer text-2xl">
          <a
            href="#"
            @click="toggleLocales"
            class="footer-link text-cyan-700 hover:text-cyan-500"
            :title="t('toggle_language')"
          >
            <i class="iconify" :data-icon="'ant-design:translation-outlined'" />
          </a>
        </li>
        <li class="cursor-pointer text-2xl">
          <a
            href="#"
            @click="toggleDark"
            class="text-cyan-700 hover:text-cyan-500"
            :title="t('toggle_theme')"
          >
            <i class="iconify" :data-icon="'mdi:theme-light-dark'" />
          </a>
        </li>
        <li class="cursor-pointer text-2xl">
          <a
            href="https://github.com/itorets"
            rel="noreferrer"
            target="_blank"
            class="footer-link text-cyan-700 hover:text-cyan-500"
            title="Github repo"
          >
            <i class="iconify" :data-icon="'mdi:github'" />
          </a>
        </li>
      </ul>

      <span class="text-xs"
        >{{ t('made_by') }}
        <a
          class="footer-link text-cyan-400 hover:text-cyan-500"
          href="https://github.com/alvarosaburido"
          rel="noreferrer"
          target="_blank"
          >Alvaro Saburido</a
        ></span
      >
    </footer>
  </div>
</template>

<style>
a,
.footer-link {
  @apply transition-all ease-out duration-100;
}

.footer-link {
  opacity: 0.8;
}
</style>
