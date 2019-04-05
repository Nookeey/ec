<template>
    <div class="wrapper">
      <nav>
        <ul>
          <li @click="setActive('modules')" :class="{ active: isActive('modules') }">Modules</li>
          <li @click="setActive('styles')" :class="{ active: isActive('styles') }">Styles</li>
        </ul>
      </nav>

      <div class="modules-wrapper">

        <div :class="[ { active: isActiveModule('modules') }, 'modules-wrapper modules']">
          <ul>
            <li v-for="(module, index) in modules" :key="index" @click="$emit('moduleID', index)">
              <img v-if="module !== 'Preheder'" :src="require('~/assets/img/' + module + '.jpg')" :alt="module" class="module-img">
            </li>
          </ul>
        </div>

        <div :class="[ { active: isActiveModule('styles') }, 'modules-wrapper styles']">
          <ul>

            <div v-for="(value, key, index) in moduleConfig" :key="index">

              <div class="tag-wrapper">
                <div v-for="(tag, key, index) in value" :key="index">

                  <!-- TAG -->
                  <h6 class="tag-title">{{ key }}</h6>
                  <!-- TAG - END -->

                  <div v-for="(style, key, index) in tag" :key="index">

                    <!-- TEXT -->
                    <textarea v-if="key === 'text'" name="" id="" cols="30" rows="5" v-model="tag[key]"></textarea>
                    <!-- TEXT - END -->

                    <!-- IMG -->
                    <img v-if="key == 'src'" :src="tag['src']" :alt="tag['alt']" class="img-prev">
                    <li v-if="key == 'src'" class="form-control">
                      <span class="style-title">{{ key }}</span>
                      <textarea class="style-input" type="text" v-model="tag['src']"></textarea>
                    </li>
                    <!-- IMG - END -->

                    <!-- STYLE -->
                    <div v-if="key === 'style'" class="style-wrapper">
                      <li v-for="(s, key, index) in style" :key="index" class="form-control">
                        <span v-if="key !== 'fontSize'" class="style-title">{{ key }}</span>
                        <input class="style-input" type="text" v-model="style[key]">
                      </li>
                    </div>
                    <!-- STYLE - END -->

                    <!-- SLIDER -->
                    <div v-if="key === 'slider'" class="style-wrapper">
                      <li v-for="(s, key, index) in style" :key="index" class="form-control">
                        <span class="style-title">{{ key }}</span>
                        <vue-slider v-model="style[key]" :min="8" :max="60" style="width: 120px;"></vue-slider>
                        <span class="slider-value">{{ style[key] }}</span>
                      </li>
                    </div>
                    <!-- SLIDER - END -->

                  </div>

                  <!-- BUTTON -->
                  <button @click="$emit('emitShowModalAddStyle'), setTagName('h', key)">Select style</button>
                  <button @click="appendToJson">Add</button>
                  <!-- BUTTON - END -->

                </div>
              </div>

            </div>

          </ul>
        </div>

      </div>

    </div>
</template>

<script>
import VueSlider from 'vue-slider-component/dist-css/vue-slider-component.umd.min.js'
import 'vue-slider-component/dist-css/vue-slider-component.css'
import 'vue-slider-component/theme/default.css'

export default {
  props: {
    moduleConfig: {
      type: Object
    },
    modules: {
      type: Array
    },
    checkedStyles: {
      type: Array
    }
  },
  components: {
    VueSlider
  },
  data () {
    return {
      activeItem: null,
      activeModule: null,
      dropdownItem: null,
      sliderValue: 20,
      tagName1: null,
      tagName2: null,
     }
  },
  methods: {
    isActive (menuItem) {
      return this.activeItem === menuItem
    },
    setActive (menuItem) {
      this.activeItem = menuItem
      this.setActiveModule(menuItem)
    },
    isDropdown (item) {
      return this.dropdownItem === item
    },
    setDropdown (item) {
      this.dropdownItem = item
    },
    isActiveModule (module) {
      return this.activeModule == module
    },
    setActiveModule (module)  {
      this.activeModule = module
    },
    setTagName (tag1, tag2) {
      this.tagName1 = tag1
      this.tagName2 = tag2
    },
    appendToJson () {
      let newStyle = {}
      this.checkedStyles.forEach(e => {
        newStyle[e.name] = e.value
        this.moduleConfig[this.tagName1][this.tagName2]['style'] = {
          ...this.moduleConfig[this.tagName1][this.tagName2]['style'],
          ...newStyle
        }
      });
    }
  }
}
</script>

<style scoped>
  * { box-sizing: border-box; font-family: 'Montserrat', sans-serif; font-weight: 300; }

  nav { width: 250px; height: 100%; background: #1b1b1b; position: fixed; top: 0; left: 0; border-right: 1px solid #585858; z-index: 100; }
  nav ul { margin: 0; padding: 0; }
  nav li { display: block; padding: 18px; margin: 0px; border-top: solid 1px #292929; border-left: 4px solid transparent; outline: none !important; text-transform: uppercase; color: #ffffff; font-size: 13px; text-decoration: none; font-weight: 400; cursor: pointer; }
  nav li:hover { font-weight: 700; background: #202020; }
  nav li.active { border-left: 4px solid #3498db; font-weight: 700; background: #202020; }


	.modules-wrapper { width: 300px; height: 100%; background: #202020; position: fixed; top: 0; left: -50px; transition: all .3s ease; overflow-y: scroll; z-index: 1; }
	.modules-wrapper.active { left: 250px; }


  .modules ul { margin: 0; padding: 0; }
  .modules li { min-height: 50px; color: #ffffff; border-bottom: solid 1px #2c2c2c; border-left: 4px solid transparent; padding: 10px 20px; font-size: 13px; cursor: pointer; }
  .modules li:hover { color: #ffffff; border-left: 4px solid #3498db; }
  .modules .module-img { max-width: 300px; width: 100%; }


  .styles ul { margin: 0; padding: 15px; }
	.styles textarea { width: 100%; resize: none; border-radius: 6px; border: none; padding: 6px; margin: .7em 0; }
  .styles h6 { color: #ffffff; font-weight: 600; }
  .styles li.form-control { min-height: 50px; color: #ffffff; border-bottom: solid 1px #2c2c2c; padding: 0; font-size: 13px; display: flex; align-items: center; justify-content: space-between; padding: .7em 0; }
  .styles span.style-title { font-size: 12px; }
  .styles input.style-input { border: 0px; border-radius: 5px; cursor: pointer; color: #000000 !important; width: 120px; height: 32px; top: -7px; padding: 0px; text-align: center; outline: none; font-size: 11px; }
  .styles .tag-wrapper { margin: 2em 0; }
  .styles .tag-title { font-size: 1em; color: #3498db !important; font-weight: 600; margin: 0; }
  .styles .style-wrapper { margin: .7em 0 0; }
  .styles .li-textarea { width: 85% !important; }
  .styles .img-prev { display: block; margin: 0 auto; max-width: 140px; }  
  .styles .slider-value { background: #3498db; padding: 2px 4px; border-radius: 4px; }  

</style>
