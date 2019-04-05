<template>
  <tr @mouseover="showButton=true" @mouseleave="hideButton" @click="$emit('emitModuleConfig', moduleConfig)">
    <td :style="moduleConfig.td.td_wrapper.style">
      <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
        <tr>
          <td :style="[moduleConfig.td.td_main.style, { fontSize: moduleConfig.td.td_main.slider.fontSize+'px' }]">
            <p :style="moduleConfig.p.p_1.style" v-html="moduleConfig.p.p_1.text"/>
          </td>
        </tr>
      </table>
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
              backgroundColor: '#ffffff',
            }
          },
          td_main: {
            style: {
              margin: '',
              padding: '20px',
              fontFamily: 'sans-serif',
              fontWeight: '400',
              lineHeight: '20px',
              color: '#000000',
            },
            slider: {
              fontSize: '15',
            }
          },
        },
        p: {
          p_1: {
            text: 'Maecenas sed ante pellentesque, posuere leo id, eleifend dolor. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Praesent laoreet malesuada cursus. Maecenas scelerisque congue eros eu posuere. Praesent in felis ut velit pretium lobortis rhoncus ut&nbsp;erat.',
            style: {
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
      }, 100);
    }
  },
  created () {
  }
}
</script>

<style>

</style>
