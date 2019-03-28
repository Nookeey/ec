<template>
  <tr @mouseover="showButton=true" @mouseleave="hideButton">
    <td valign="middle"
      style="text-align: center; background-image: url('https://via.placeholder.com/600x230/222222/666666'); background-color: #222222; background-position: center center !important; background-size: cover !important;">
      <div>
        <table role="presentation" border="0" cellpadding="0" cellspacing="0" width="100%">
          <tr>
            <td valign="middle"
              style="text-align: center; padding: 40px; font-family: sans-serif; font-size: 15px; line-height: 20px; color: #ffffff;">
              <p style="margin: 0;">Maecenas sed ante pellentesque, posuere leo id, eleifend dolor. Class aptent
                taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Praesent laoreet
                malesuada cursus. Maecenas scelerisque congue eros eu posuere. Praesent in felis ut velit pretium
                lobortis rhoncus ut&nbsp;erat.</p>
            </td>
          </tr>
        </table>
      </div>
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
