<template>
  <tr @mouseover="showButton=true" @mouseleave="hideButton">
    <td style="padding: 10px; background-color: #ffffff;">
      <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
        <tr>
          <td valign="top" width="50%" class="stack-column-center">
            <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
              <tr>
                <td style="padding: 10px; text-align: center">
                  <img src="https://via.placeholder.com/270" width="270" height="" alt="alt_text" border="0"
                    style="width: 100%; max-width: 270px; height: auto; background: #dddddd; font-family: sans-serif; font-size: 15px; line-height: 15px; color: #555555;">
                </td>
              </tr>
              <tr>
                <td
                  style="font-family: sans-serif; font-size: 15px; line-height: 20px; color: #555555; padding: 0 10px 10px; text-align: left;"
                  class="center-on-narrow">
                  <p style="margin: 0;">Maecenas sed ante pellentesque, posuere leo id, eleifend dolor. Class aptent
                    taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos.</p>
                </td>
              </tr>
            </table>
          </td>
          <td valign="top" width="50%" class="stack-column-center">
            <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
              <tr>
                <td style="padding: 10px; text-align: center">
                  <img src="https://via.placeholder.com/270" width="270" height="" alt="alt_text" border="0"
                    style="width: 100%; max-width: 270px; height: auto; background: #dddddd; font-family: sans-serif; font-size: 15px; line-height: 15px; color: #555555;">
                </td>
              </tr>
              <tr>
                <td
                  style="font-family: sans-serif; font-size: 15px; line-height: 20px; color: #555555; padding: 0 10px 10px; text-align: left;"
                  class="center-on-narrow">
                  <p style="margin: 0;">Maecenas sed ante pellentesque, posuere leo id, eleifend dolor. Class aptent
                    taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos.</p>
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
