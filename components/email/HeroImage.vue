<template>
    <tr @mouseover="showButton=true" @mouseleave="hideButton">
      <td style="background-color: #ffffff;">
        <img src="https://via.placeholder.com/1200x600" width="600" height="" alt="alt_text" border="0" style="width: 100%; max-width: 600px; height: auto; background: #dddddd; font-family: sans-serif; font-size: 15px; line-height: 15px; color: #555555; margin: auto; display: block;" class="g-img">
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
      }, 500);
    }
  }
}
</script>

