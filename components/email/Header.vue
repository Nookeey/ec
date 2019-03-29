<template>
    <tr @mouseover="showButton=true" @mouseleave="hideButton">
        <td bgcolor="#ffffff" style="padding: 10px 15px 10px; text-align: center;">
            <h1 style="margin: 0; font-family: Open sans condensed; font-size: 12px; color: #505050; text-decoration: underline; font-weight: normal;"><a href="$preview$" style="color: #505050;">Kliknij tutaj, jeśli mail nie wyświetla się poprawnie</a></h1>
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
