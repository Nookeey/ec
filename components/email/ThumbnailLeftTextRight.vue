<template>
  <tr @mouseover="showButton=true" @mouseleave="hideButton">
    <td dir="ltr" width="100%" style="padding: 10px; background-color: #ffffff;">
      <table role="presentation" border="0" cellpadding="0" cellspacing="0" width="100%">
        <tr>
          <td width="33.33%" class="stack-column-center">
            <table role="presentation" border="0" cellpadding="0" cellspacing="0" width="100%">
              <tr>
                <td dir="ltr" valign="top" style="padding: 0 10px;">
                  <img src="https://via.placeholder.com/170" width="170" height="170" alt="alt_text" border="0"
                    class="center-on-narrow"
                    style="height: auto; background: #dddddd; font-family: sans-serif; font-size: 15px; line-height: 15px; color: #555555;">
                </td>
              </tr>
            </table>
          </td>
          <td width="66.66%" class="stack-column-center">
            <table role="presentation" border="0" cellpadding="0" cellspacing="0" width="100%">
              <tr>
                <td dir="ltr" valign="top"
                  style="font-family: sans-serif; font-size: 15px; line-height: 20px; color: #555555; padding: 10px; text-align: left;"
                  class="center-on-narrow">
                  <h2
                    style="margin: 0 0 10px 0; font-family: sans-serif; font-size: 18px; line-height: 22px; color: #333333; font-weight: bold;">
                    Class aptent taciti sociosqu</h2>
                  <p style="margin: 0 0 10px 0;">Maecenas sed ante pellentesque, posuere leo id, eleifend dolor. Class
                    aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos.</p>
                  <table role="presentation" cellspacing="0" cellpadding="0" border="0" class="center-on-narrow"
                    style="float:left;">
                    <tr>
                      <td class="button-td button-td-primary" style="border-radius: 4px; background: #222222;">
                        <a class="button-a button-a-primary" href="https://google.com/"
                          style="background: #222222; border: 1px solid #000000; font-family: sans-serif; font-size: 15px; line-height: 15px; text-decoration: none; padding: 13px 17px; color: #ffffff; display: block; border-radius: 4px;">Primary
                          Button</a>
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
