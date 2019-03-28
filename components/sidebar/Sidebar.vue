<template>
    <div class="wrapper">
      <nav>

        <ul>
          <li id="edit-link">
            <p @click="setDropdown('edit')" class="title-link">[] Edit</p>
            <ul class="dropdown-contnet" :class="{ show: isDropdown('edit') }">
              <li @click="setActive('modules')" :class="{ active: isActive('modules') }">Modules</li>
              <li @click="setActive('styles')" :class="{ active: isActive('styles') }">Styles</li>
            </ul>
          </li>
          <li id="preview-link">
            <p @click="setDropdown('preview')" class="title-link">[] Preview</p> 
            <ul class="dropdown-contnet" :class="{ show: isDropdown('preview') }">
              <li @click="setActive('fullscreen')" :class="{ active: isActive('fullscreen') }">Fullscreen</li>
              <li @click="setActive('mobile')" :class="{ active: isActive('mobile') }">Mobile</li>
            </ul>
          </li>
        </ul>
      </nav>

      <div class="modules-wrapper">

        <div :class="[ { active: isActiveModule('modules') }, 'modules-wrapper modules']">
          <ul>
            <li v-for="(module, index) in modules" :key="index" @click="$emit('moduleID', index)">{{ module }}</li>
          </ul>
        </div>

        <div :class="[ { active: isActiveModule('styles') }, 'modules-wrapper styles']">
          <ul>

            <li v-for="(value, key, index) in moduleConfig" :key="index">

              <div v-if="key === 'td' || key === 'ul'">
                <div v-for="(val, key, index) in value" :key="index" style="padding-bottom: 50px">
                  <div v-for="(v, key, index) in val" :key="index" class="form-control">
                      <span>{{ key }}</span>
                      <input type="text" v-model="val[key]">
                  </div>
                </div>
              </div>

              <div v-if="key === 'h1' || key === 'p'">
                <div v-for="(val, key, index) in value" :key="index" class="form-control">
                  <textarea v-if="key === 'text'" name="" id="" cols="30" rows="10" v-model="value[key]"></textarea>
                  <div v-if="key === 'style'">
                    <div v-for="(v, key, index) in val" :key="index" class="form-control">
                      <span>{{ key }}</span>
                      <input type="text" v-model="val[key]">
                    </div>
                  </div>
                </div>
              </div>

              <!-- <div v-if="key === 'ul'">
                <div v-for="(val, key, index) in value" :key="index">
                  <div v-for="(v, key, index) in val" :key="index">
                    <div class="form-control">
                      <span>{{ key }}</span>
                      <input type="text" v-model="val[key]">
                    </div>
                  </div>
                </div>
              </div> -->

              <div v-if="key === 'li'">
                <div v-for="(val, key, index) in value" :key="index">
                  <div v-if="key === 'text'">
                    <div v-for="(v, key, index) in val" :key="index">
                      <div class="form-control">
                        <span>{{ key }}</span>
                        <input type="text" v-model="val[key]">
                      </div>
                    </div>
                  </div>
                  <div v-if="key === 'style'">
                    <div v-for="(v, key, index) in val" :key="index">
                      <div class="form-control">
                        <span>{{ key }}</span>
                        <input type="text" v-model="val[key]">
                      </div>
                    </div>
                  </div>
                </div>
              </div>

            </li>

          </ul>
        </div>

      </div>

    </div>
</template>

<script>
export default {
  props: {
    moduleConfig: {
      type: Object
    },
    modules: {
      type: Array
    }
  },
  data () {
    return {
      activeItem: null,
      activeModule: null,
      dropdownItem: null,
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
  }
}
</script>

<style scoped>
  * { box-sizing: border-box; font-family: 'Montserrat', sans-serif; font-weight: 300; }

  nav { width: 250px; height: 100%; background: #2b2e33; position: fixed; top: 0; left: 0; border-right: 1px solid #585858; z-index: 100; }
  nav ul { margin: 0; padding: 0; }
  nav li { width: 100%; color: #828282; font-size: 14px; cursor: pointer; list-style: none; }
  nav p.title-link { color: #828282; padding: 12px 0 12px 25px; margin: 0; }
  nav p.title-link:hover,
  nav ul.dropdown-contnet li:hover { color: #ffffff; }
  nav ul.dropdown-contnet { display: none; transition: all .3s ease; }
  nav ul.dropdown-contnet.show { display: grid; }
  nav ul.dropdown-contnet li { padding: 12px 0 12px 50px; border-left: 4px solid transparent; }
  nav ul.dropdown-contnet li.active { border-left: 4px solid #68c0b0; }


	.modules-wrapper { width: 300px; height: 100%; background: #2b2e33; position: fixed; top: 0; left: -50px; transition: all .3s ease; overflow-y: scroll; z-index: 1; }
	.modules-wrapper.active { left: 250px; }


  .modules ul { margin: 0; padding: 0; }
  .modules li { color: #828282; width: 100%; padding: 12px 22px; border-left: 4px solid transparent; font-size: 14px; cursor: pointer; }
  .modules li:hover { color: #ffffff; border-left: 4px solid #68c0b0; }


  .styles ul { margin: 0; padding: 15px; }
	.styles li { color: #828282; list-style: none; }
	.styles textarea { width: 100%; resize: none; }

</style>
