<template>
  <tr @mouseover="showButton=true" @mouseleave="hideButton" @click="$emit('emitModuleConfig', moduleConfig)">
    <td valign="top" class="mcnTextBlockInner footer" :style="moduleConfig.td.td_wrapper.style">
      <center :style="moduleConfig.a.a_1.style">
        <!--<a href="$opt-out$">-->
        <a :style="moduleConfig.a.a_1.style" :href="moduleConfig.a.a_1.href" target="_blank" v-html="moduleConfig.a.a_1.text"></a>
      </center>
    </td>
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
              padding: '15px 0',
            }
          }
        },
        a: {
          a_1: {
            text: 'Jeśli nie chcesz już otrzymywać newslettera kliknij tutaj.',
            href: '$opt-out$',
            style: {
              color: '#999',
              textDecoration: 'underline',
            }
          }
        },
      }
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
