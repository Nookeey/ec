<template>
  <table align="center" role="presentation" cellspacing="0" cellpadding="0" border="0" width="600" style="margin: auto;"
    class="email-container" @mouseover="showButton=true" @mouseleave="hideButton">
     <tr>
        <td valign="top" class="mcnTextBlockInner footer" style="background: #ffffff; padding: 15px 0;">
          <center style="color: #999;"><!--<a href="$opt-out$">--> Jeśli nie chcesz już otrzymywać newslettera kliknij <a style="color: #999; text-decoration: underline;" href="$opt-out$" target="_blank">tutaj.</a></center>
        </td>
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
