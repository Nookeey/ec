<template>
  <tr @mouseover="showButton=true" @mouseleave="hideButton" @click="$emit('emitModuleConfig', moduleConfig)">
    <td :style="moduleConfig.td.td_wrapper">
      <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
        <tr>
          <td valign="top" width="33.33%" class="stack-column-center">
            <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
              <tr>
                <td :style="moduleConfig.td.td_img_1">
                  <img :src="moduleConfig.img.img_1.src" :width="moduleConfig.img.img_1.style.maxWidth" height="" :alt="moduleConfig.img.img_1.alt" border="0" :style="moduleConfig.img.img_1.style">
                </td>
              </tr>
              <tr>
                <td :style="moduleConfig.td.td_text_1" class="center-on-narrow">
                  <p :style="moduleConfig.p.p_1.style" v-html="moduleConfig.p.p_1.text"></p>
                </td>
              </tr>
            </table>
          </td>
          <td valign="top" width="33.33%" class="stack-column-center">
            <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
              <tr>
                <td :style="moduleConfig.td.td_img_2">
                  <img :src="moduleConfig.img.img_2.src" :width="moduleConfig.img.img_2.style.maxWidth" height="" :alt="moduleConfig.img.img_2.alt" border="0" :style="moduleConfig.img.img_2.style">
                </td>
              </tr>
              <tr>
                <td :style="moduleConfig.td.td_text_2" class="center-on-narrow">
                  <p :style="moduleConfig.p.p_2.style" v-html="moduleConfig.p.p_2.text"></p>
                </td>
              </tr>
            </table>
          </td>
          <td valign="top" width="33.33%" class="stack-column-center">
            <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
              <tr>
                <td :style="moduleConfig.td.td_img_3">
                  <img :src="moduleConfig.img.img_3.src" :width="moduleConfig.img.img_3.style.maxWidth" height="" :alt="moduleConfig.img.img_3.alt" border="0" :style="moduleConfig.img.img_3.style">
                </td>
              </tr>
              <tr>
                <td :style="moduleConfig.td.td_text_3" class="center-on-narrow">
                  <p :style="moduleConfig.p.p_3.style" v-html="moduleConfig.p.p_3.text"></p>
                </td>
              </tr>
            </table>
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
            padding: '10px',
            backgroundColor: '#ffffff',
          },
          td_img_1: {
            padding: '10px',
            textAlign: 'center',
          },
          td_text_1: {
            fontFamily: 'sans-serif',
            fontSize: '15px',
            lineHeight: '20px',
            color: '#555555',
            padding: '0 10px 10px',
            textAlign: 'left',
          },
          td_img_2: {
            padding: '10px',
            textAlign: 'center',
          },
          td_text_2: {
            fontFamily: 'sans-serif',
            fontSize: '15px',
            lineHeight: '20px',
            color: '#555555',
            padding: '0 10px 10px',
            textAlign: 'left',
          },
          td_img_3: {
            padding: '10px',
            textAlign: 'center',
          },
          td_text_3: {
            fontFamily: 'sans-serif',
            fontSize: '15px',
            lineHeight: '20px',
            color: '#555555',
            padding: '0 10px 10px',
            textAlign: 'left',
          },
        },
        img: {
          img_1: {
            src: 'https://via.placeholder.com/170',
            alt: 'alt_text',
            style: {
              width: '100%',
              maxWidth: '170px',
              height: 'auto',
              background: '#dddddd',
            }
          },
          img_2: {
            src: 'https://via.placeholder.com/170',
            alt: 'alt_text',
            style: {
              width: '100%',
              maxWidth: '170px',
              height: 'auto',
              background: '#dddddd',
            }
          },
          img_3: {
            src: 'https://via.placeholder.com/170',
            alt: 'alt_text',
            style: {
              width: '100%',
              maxWidth: '170px',
              height: 'auto',
              background: '#dddddd',
            }
          },
        },
        p: {
          p_1: {
            text: 'Maecenas sed ante pellentesque, posuere leo id, eleifend dolor. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos.',
            style: {
              margin: '0',
            }
          },
          p_2: {
            text: 'Maecenas sed ante pellentesque, posuere leo id, eleifend dolor. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos.',
            style: {
              margin: '0',
            }
          },
          p_3: {
            text: 'Maecenas sed ante pellentesque, posuere leo id, eleifend dolor. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos.',
            style: {
              margin: '0',
            }
          },
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
