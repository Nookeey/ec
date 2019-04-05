<template>
  <div class="modal-wrapper">
    <div class="modal">
      <div class="modal-title">
        Title
      </div>
      <div class="modal-body">
        <input id="search" type="text" v-model="search" placeholder="search">
        <ul>
          <li v-for="(style, index) in filteredStyles" :key="index">
            <input type="checkbox" v-model="checkedStyles" :value="style">
            <label @click="style.checked = !style.checked"><strong>{{ style.name }}</strong>: {{ style.value }}</label>
          </li>
        </ul>
      </div>
      <div class="moda-footer">
        <button class="btn-cancel" @click="$emit('closeModal')">Cancel</button>
        <button class="btn-submit" @click="emitCheckedStyles">Add</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      search: '',
      styles: [
        { name: 'animation', value: 'none', },
        { name: 'animation-delay', value: '0', },
        { name: 'animation-direction', value: 'normal', },
        { name: 'animation-duration', value: '0', },
        { name: 'animation-fill-mode', value: 'none', },
        { name: 'animation-iteration-count', value: '1', },
        { name: 'animation-name', value: 'none', },
        { name: 'animation-play-state', value: 'running', },
        { name: 'animation-timing-function', value: 'ease', },
        { name: 'backface-visibility', value: 'visible', },
        { name: 'background', value: '0', },
        { name: 'background-attachment', value: 'scroll', },
        { name: 'background-clip', value: 'border-box', },
        { name: 'background-color', value: 'transparent', },
        { name: 'background-image', value: 'none', },
        { name: 'background-origin', value: 'padding-box', },
        { name: 'background-position', value: '0 0', },
        { name: 'background-position-x', value: '0', },
        { name: 'background-position-y', value: '0', },
        { name: 'background-repeat', value: 'repeat', },
        { name: 'background-size', value: 'auto auto', },
        { name: 'border', value: '0', },
        { name: 'border-style', value: 'none', },
        { name: 'border-width', value: 'medium', },
        { name: 'border-color', value: 'inherit', },
        { name: 'border-bottom', value: '0', },
        { name: 'border-bottom-color', value: 'inherit', },
        { name: 'border-bottom-left-radius', value: '0', },
        { name: 'border-bottom-right-radius', value: '0', },
        { name: 'border-bottom-style', value: 'none', },
        { name: 'border-bottom-width', value: 'medium', },
        { name: 'border-collapse', value: 'separate', },
        { name: 'border-image', value: 'none', },
        { name: 'border-left', value: '0', },
        { name: 'border-left-color', value: 'inherit', },
        { name: 'border-left-style', value: 'none', },
        { name: 'border-left-width', value: 'medium', },
        { name: 'border-radius', value: '0', },
        { name: 'border-right', value: '0', },
        { name: 'border-right-color', value: 'inherit', },
        { name: 'border-right-style', value: 'none', },
        { name: 'border-right-width', value: 'medium', },
        { name: 'border-spacing', value: '0', },
        { name: 'border-top', value: '0', },
        { name: 'border-top-color', value: 'inherit', },
        { name: 'border-top-left-radius', value: '0', },
        { name: 'border-top-right-radius', value: '0', },
        { name: 'border-top-style', value: 'none', },
        { name: 'border-top-width', value: 'medium', },
        { name: 'bottom', value: 'auto', },
        { name: 'box-shadow', value: 'none', },
        { name: 'box-sizing', value: 'content-box', },
        { name: 'caption-side', value: 'top', },
        { name: 'clear', value: 'none', },
        { name: 'clip', value: 'auto', },
        { name: 'color', value: 'inherit', },
        { name: 'columns', value: 'auto', },
        { name: 'column-count', value: 'auto', },
        { name: 'column-fill', value: 'balance', },
        { name: 'column-gap', value: 'normal', },
        { name: 'column-rule', value: 'medium none currentColor', },
        { name: 'column-rule-color', value: 'currentColor', },
        { name: 'column-rule-style', value: 'none', },
        { name: 'column-rule-width', value: 'none', },
        { name: 'column-span', value: '1', },
        { name: 'column-width', value: 'auto', },
        { name: 'content', value: 'normal', },
        { name: 'counter-increment', value: 'none', },
        { name: 'counter-reset', value: 'none', },
        { name: 'cursor', value: 'auto', },
        { name: 'direction', value: 'ltr', },
        { name: 'display', value: 'inline', },
        { name: 'empty-cells', value: 'show', },
        { name: 'float', value: 'none', },
        { name: 'font', value: 'normal', },
        { name: 'font-family', value: 'inherit', },
        { name: 'font-size', value: 'medium', },
        { name: 'font-style', value: 'normal', },
        { name: 'font-variant', value: 'normal', },
        { name: 'font-weight', value: 'normal', },
        { name: 'height', value: 'auto', },
        { name: 'hyphens', value: 'none', },
        { name: 'left', value: 'auto', },
        { name: 'letter-spacing', value: 'normal', },
        { name: 'line-height', value: 'normal', },
        { name: 'list-style', value: 'none', },
        { name: 'list-style-image', value: 'none', },
        { name: 'list-style-position', value: 'outside', },
        { name: 'list-style-type', value: 'disc', },
        { name: 'margin', value: '0', },
        { name: 'margin-bottom', value: '0', },
        { name: 'margin-left', value: '0', },
        { name: 'margin-right', value: '0', },
        { name: 'margin-top', value: '0', },
        { name: 'max-height', value: 'none', },
        { name: 'max-width', value: 'none', },
        { name: 'min-height', value: '0', },
        { name: 'min-width', value: '0', },
        { name: 'opacity', value: '1', },
        { name: 'orphans', value: '0', },
        { name: 'outline', value: '0', },
        { name: 'outline-color', value: 'invert', },
        { name: 'outline-style', value: 'none', },
        { name: 'outline-width', value: 'medium', },
        { name: 'overflow', value: 'visible', },
        { name: 'overflow-x', value: 'visible', },
        { name: 'overflow-y', value: 'visible', },
        { name: 'padding', value: '0', },
        { name: 'padding-bottom', value: '0', },
        { name: 'padding-left', value: '0', },
        { name: 'padding-right', value: '0', },
        { name: 'padding-top', value: '0', },
        { name: 'page-break-after', value: 'auto', },
        { name: 'page-break-before', value: 'auto', },
        { name: 'page-break-inside', value: 'auto', },
        { name: 'perspective', value: 'none', },
        { name: 'perspective-origin', value: '50% 50%', },
        { name: 'position', value: 'static', },
        { name: 'right', value: 'auto', },
        { name: 'tab-size', value: '8', },
        { name: 'table-layout', value: 'auto', },
        { name: 'text-align', value: 'inherit', },
        { name: 'text-align-last', value: 'auto', },
        { name: 'text-decoration', value: 'none', },
        { name: 'text-decoration-color', value: 'inherit', },
        { name: 'text-decoration-line', value: 'none', },
        { name: 'text-decoration-style', value: 'solid', },
        { name: 'text-indent', value: '0', },
        { name: 'text-shadow', value: 'none', },
        { name: 'text-transform', value: 'none', },
        { name: 'top', value: 'auto', },
        { name: 'transform', value: 'none', },
        { name: 'transform-style', value: 'flat', },
        { name: 'transition', value: 'none', },
        { name: 'transition-delay', value: '0s', },
        { name: 'transition-duration', value: '0s', },
        { name: 'transition-property', value: 'none', },
        { name: 'transition-timing-function', value: 'ease', },
        { name: 'unicode-bidi', value: 'normal', },
        { name: 'vertical-align', value: 'baseline', },
        { name: 'visibility', value: 'visible', },
        { name: 'white-space', value: 'normal', },
        { name: 'widows', value: '0', },
        { name: 'width', value: 'auto', },
        { name: 'word-spacing', value: 'normal', },
        { name: 'z-index', value: 'auto', },
      ],
      checkedStyles: [],
    }
  },
  created () {
  },
  computed: {
    filteredStyles () {
      return this.styles.filter(style => style.name.includes(this.search))
    }
  },
  methods: {
    emitCheckedStyles () {
      this.$emit('emitCheckedStyles', this.checkedStyles)
    }
  }
}
</script>

<style scoped>
  * { box-sizing: border-box; font-family: 'Montserrat', sans-serif; font-weight: 300; }
  strong { font-weight: 600; }

  .modal-wrapper { position: fixed; top: 0; left: 0; display: flex; align-items: center; background: rgba(255, 255, 255, 0.18); width: 100%; height: 100vh;  z-index: 200; }

  .modal { max-width: 600px; width: 100%; height: auto; background: #ffffff; margin: 0 auto; position: relative; z-index: 300; }
  .modal { border-radius: 12px; box-shadow: 0 0 2px 0 #ffffff; border: 1px solid rgba(0,0,0,.2); }

  .modal-title,
  .modal-body { border-bottom: 1px solid #dee2e6; }

  .modal-title { font-size: 1.2em; color: #3498db; font-weight: 600; padding: 15px; }

  .modal-body { padding: 15px; }
  .modal-body #search { display: block; width: 100%; height: 40px; border: none; border-bottom: 1px solid #e9e9e9; transition: border-bottom .3s ease; }
  .modal-body #search:focus,
  .modal-body #search:active { border-bottom: 1px solid #3498db; outline: none; }
  .modal-body ul { margin: 1em 0; padding: 0; list-style: none; max-height: 300px; overflow-y: scroll; }
  .modal-body li { display: grid; grid-template-columns: 15px 1fr; grid-column-gap: 10px; align-items: center; cursor: pointer; margin: .5em 0; font-size: .9em; }
  .modal-body label { cursor: pointer; }
  .modal-body .tick { width: 15px; height: 15px; border: 1px solid #ececec; }
  .modal-body .tick.active { background: #1e7e34; }

  .moda-footer { padding: 15px; display: flex; align-items: center; justify-content: flex-end; }
  .moda-footer .btn-submit, 
  .moda-footer .btn-cancel { font-size: .8em; font-weight: 600; text-align: center; border: none; border-radius: 3px; padding: 8px 14px; cursor: pointer; margin-left: 15px; color: #ffffff; }
  .moda-footer .btn-submit { background: #1e7e34; }
  .moda-footer .btn-cancel { background: #dc3545; }
</style>
