<template>
    <tr @mouseover="showButton=true" @mouseleave="hideButton" @click="$emit('emitModuleConfig', moduleConfig)">
      <td :style="moduleConfig.td.td_wrapper.style">
        <img :src="moduleConfig.img.hero_img.src" :width="moduleConfig.img.hero_img.style.maxWidth" height="" alt="alt_text" border="0" :style="moduleConfig.img.hero_img.style" class="g-img">
      </td>
      <!-- <ButtonModule @mouseover="showButton=true" v-if="showButton" @removeModule="$emit('removeModule', id)"/> -->
    </tr>
</template>

<script>
import ButtonModule from '@/components/ui/ButtonModule';

export default {
  props: {
    id: {
      type: Number
    }
  },
  components: {
    ButtonModule
  },
  data () {
    return {
      showButton: false,
      moduleConfig: {
        td: {
          td_wrapper: {
            style: {
              background: '#ffffff',
            }
          },
        },
        img: {
          hero_img: {
            src: 'https://via.placeholder.com/1200x600',
            style: {
              width: '100%',
              maxWidth: '600px',
              height: 'auto',
              background: '#dddddd',
              margin: 'auto',
              display: 'block',
            }
          }
        },
      },
    }
  },
  methods: {
    hideButton() {
      setTimeout(() => {
        this.showButton = false
      }, 500);
    }
  }
}
</script>
