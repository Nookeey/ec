<template>
  <tr @mouseover="showButton=true" @mouseleave="hideButton" @click="$emit('emitModuleConfig', moduleConfig)">
    <td dir="ltr" width="100%" :style="moduleConfig.td.td_wrapper">
      <table role="presentation" border="0" cellpadding="0" cellspacing="0" width="100%">
        <tr>
          <td :width="moduleConfig.td.td_left.width" class="stack-column-center">
            <table role="presentation" border="0" cellpadding="0" cellspacing="0" width="100%">
              <tr>
                <td dir="ltr" valign="top" :style="moduleConfig.td.td_left_img">
                  <img :src="moduleConfig.img.img_1.src" :width="moduleConfig.img.img_1.style.maxWidth" height="auto" :alt="moduleConfig.img.img_1.alt" border="0" class="center-on-narrow" :style="moduleConfig.img.img_1.style">
                </td>
              </tr>
            </table>
          </td>
          <td :width="moduleConfig.td.td_right.width" class="stack-column-center">
            <table role="presentation" border="0" cellpadding="0" cellspacing="0" width="100%">
              <tr>
                <td dir="ltr" valign="top" :style="moduleConfig.td.td_right_text" class="center-on-narrow">
                  <h2 :style="moduleConfig.h.h2_1.style" v-html="moduleConfig.h.h2_1.text"></h2>
                  <p :style="moduleConfig.p.p_1.style" v-html="moduleConfig.p.p_1.text"></p>
                  <table role="presentation" cellspacing="0" cellpadding="0" border="0" class="center-on-narrow"
                    style="float:left;">
                    <tr>
                      <td class="button-td button-td-primary" style="border-radius: 4px; background: #222222;">
                        <a class="button-a button-a-primary" href="https://google.com/" :style="moduleConfig.button.btn_1.style">{{ moduleConfig.button.btn_1.text }}</a>
                      </td>
                    </tr>
                  </table>
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
          td_left: {
            width: '33.33%'
          },
          td_left_img: {
            padding: '0 10px'
          },
          td_right: {
            width: '66.66%'
          },
          td_right_text: {
            fontFamily: 'sans-serif',
            fontSize: '15px',
            lineHeight: '20px',
            color: '#555555',
            padding: '10px',
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
        },
        h: {
          h2_1: {
            text: 'Class aptent taciti sociosqu.',
            style: {
              margin: '0 0 10px 0',
              fontFamily: 'sans-serif',
              fontSize: '18px',
              lineHeight: '22px',
              color: '#333333',
              fontWeight: 'bold'
            }
          }
        },
        p: {
          p_1: {
            text: 'Maecenas sed ante pellentesque, posuere leo id, eleifend dolor. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos.',
            style: {
              margin: '0 0 10px 0'
            }
          },
        },
        button: {
          btn_1: {
            text: 'Centered Primary Button',
            style: {
              background: '#222222',
              border: '1px solid #000000',
              fontFamily: 'sans-serif',
              fontSize: '15px',
              lineHeight: '15px',
              textDecoration: 'none',
              padding: '13px 17px',
              color: '#ffffff',
              display: 'block',
              borderRadius: '4px'
            }
          }
        }
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
