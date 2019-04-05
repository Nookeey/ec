<template>
  <tr @mouseover="showButton=true" @mouseleave="hideButton" @click="$emit('emitModuleConfig', moduleConfig)">
    <td valign="middle" :style="moduleConfig.td.td_wrapper.style">
      <div>
        <table role="presentation" border="0" cellpadding="0" cellspacing="0" width="100%">
          <tr>
            <td valign="middle" :style="[moduleConfig.td.td_main.style, { fontSize: moduleConfig.td.td_main.slider.fontSize+'px' }]">
              <p :style="moduleConfig.p.p_1.style" v-html="moduleConfig.p.p_1.text"></p>
            </td>
          </tr>
        </table>
      </div>
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
              textAlign: 'center',
              backgroundImage: 'url("https://via.placeholder.com/600x230/222222/666666")',
              backgroundColor: '#222222',
              backgroundPosition: 'center center !important',
              backgroundSize: 'cover !important',
            }
          },
          td_main: {
            style: {
              textAlign: 'center',
              padding: '40px',
              fontFamily: 'sans-serif',
              lineHeight: '20px',
              color: '#ffffff',
            },
            slider: {
              fontSize: '15',
            }
          }
        },
        p: {
          p_1: {
            text: 'Maecenas sed ante pellentesque, posuere leo id, eleifend dolor. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Praesent laoreet malesuada cursus. Maecenas scelerisque congue eros eu posuere. Praesent in felis ut velit pretium lobortis rhoncus ut&nbsp;erat.',
            style: {
              margin: '0',
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
    },
  }
}
</script>
