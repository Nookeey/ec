<template>
  <tr @mouseover="showButton=true" @mouseleave="hideButton">
    <td aria-hidden="true" height="40" style="font-size: 0px; line-height: 0px;">
      &nbsp;
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
