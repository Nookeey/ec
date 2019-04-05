<template>
    <tr @mouseover="showButton=true" @mouseleave="hideButton" @click="$emit('emitModuleConfig', moduleConfig)">
        <td :style="moduleConfig.td.td_wrapper.style">
            <h1 :style="moduleConfig.a.a_1.style">
              <a href="$preview$" :style="[moduleConfig.a.a_1.style, { fontSize: moduleConfig.a.a_1.slider.fontSize+'px' }]" v-html="moduleConfig.a.a_1.text"></a>
            </h1>
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
              padding: '10px 15px 10px',
              textAlign: 'center',
            }
          },
        },
        a: {
          a_1: {
            text: 'Kliknij tutaj, jeśli mail nie wyświetla się poprawnie',
            href: '$preview$',
            style: {
              margin: '0',
              fontFamily: 'Open sans condensed',
              color: '#505050',
              textDecoration: 'underline',
              fontWeight: 'normal',
            },
            slider: {
              fontSize: '12',
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
  }
}
</script>
