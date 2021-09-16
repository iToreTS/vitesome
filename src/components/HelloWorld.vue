<script lang="ts">
import { defineComponent } from 'vue';
import { useI18n } from 'vue-i18n';

export default defineComponent({
  name: 'HelloWorld',
  props: {
    msg: {
      type: String,
      required: true,
    },
  },
  setup: () => {
    const { t } = useI18n();
    
    return { t };
  },
});
</script>
<template>
  <div class="text-center text-md">
    <h1 class="font-serif font-bold font-bold text-4xl mb-8">{{ msg }}</h1>

    <p>
      {{t('recomended-ide')}}
     
      
    </p>

    <p>{{t('See')}} {{t('more-info')}}</p>
    <p class="mb-10">
      
      |
      
    </p>
  </div>
</template>

<style scoped>
a {
  @apply text-cyan-400 hover:text-cyan-500 transition-all ease-out duration-100;
}
</style>

<style scoped>
label {
  margin: 0 0.5em;
  font-weight: bold;
}

code {
  @apply text-xs font-mono bg-yellow-200 text-yellow-700 rounded px-0.5 py-0.5;
}
</style>
