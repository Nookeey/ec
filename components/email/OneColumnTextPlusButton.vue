<template>
    <tr @mouseover="showButton=true" @mouseleave="hideButton" @click="$emit('emitModuleConfig', moduleConfig)">
      <td :style="moduleConfig.td[0]">
        <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
          <tr>
            <td :style="moduleConfig.td[1]">
              <h1 :style="moduleConfig.h1.style" v-html="moduleConfig.h1.text"></h1>
              <p :style="moduleConfig.p.style" v-html="moduleConfig.p.text"></p>
              <ul :style="moduleConfig.ul.style">
                <li :style="moduleConfig.li.style" v-html="moduleConfig.li.text[0]"></li>
                <li :style="moduleConfig.li.style" v-html="moduleConfig.li.text[1]"></li>
                <li :style="moduleConfig.li.style" v-html="moduleConfig.li.text[2]"></li>
              </ul>
            </td>
          </tr>
          <tr>
            <td :style="moduleConfig.td[2]">
              <table align="center" role="presentation" cellspacing="0" cellpadding="0" border="0"
                style="margin: auto;">
                <tr>
                  <td class="button-td button-td-primary" style="border-radius: 4px; background: #222222;">
                    <a class="button-a button-a-primary" href="https://google.com/" :style="moduleConfig.button.style">{{ moduleConfig.button.text }}</a>
                  </td>
                </tr>
              </table>
            </td>
          </tr>
        </table>
      </td>
    <ButtonModule @mouseover="showButton=true" v-if="showButton" @removeModule="$emit('removeModule', id)"/>
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
          0: {
            backgroundColor: '#ffffff',
          },
          1: {
            padding: '20px',
            fontFamily: 'sans-serif',
            fontSize: '15px',
            lineHeight: '20px',
            color: '#555555',
          },
          2: {
            padding: '0 20px 20px',
          }
        },
        h1: {
          text: 'Praesent laoreet malesuada&nbsp;cursus.',
          style: {
            margin: '0 0 10px', 
            fontSize: '25px', 
            lineHeight: '30px', 
            color: '#333333', 
            fontWeight: 'normal',
          }
        },
        p: {
          text: 'Maecenas sed ante pellentesque, posuere leo id, eleifend dolor. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Praesent laoreet malesuada cursus. Maecenas scelerisque congue eros eu posuere. Praesent in felis ut velit pretium lobortis rhoncus ut&nbsp;erat.',
          style: {
            margin: '0 0 10px',
          }
        },
        ul: {
          style: {
            padding: '0',
            margin: '0',
            listStyleType: 'disc',
          }
        },
        li: {
          text: {
            0: 'A list item.',
            1: 'Another list item here.',
            2: 'Everyone gets a list item, list items for everyone!',
          },
          style: {
            margin: '0 0 10px 20px',
          }
        },
        button: {
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
            borderRadius: '4px',
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
