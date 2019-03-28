<template>
  <table align="center" role="presentation" cellspacing="0" cellpadding="0" border="0" width="600" style="margin: auto;"
    class="email-container" @mouseover="showButton=true" @mouseleave="hideButton">
    <tr>
      <td
        style="padding: 20px; font-family: sans-serif; font-size: 12px; line-height: 15px; text-align: center; color: #888888;">
        <webversion style="color: #cccccc; text-decoration: underline; font-weight: bold;">View as a Web Page
        </webversion>
        <br><br>
        Company Name<br><span class="unstyle-auto-detected-links">123 Fake Street, SpringField, OR, 97477 US<br>(123)
          456-7890</span>
        <br><br>
        <unsubscribe style="color: #888888; text-decoration: underline;">unsubscribe</unsubscribe>
      </td>
      <ButtonModule @mouseover="showButton=true" v-if="showButton" @removeModule="$emit('removeModule', id)"/>
    </tr>
  </table>
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
