<template>
  <section class="main-wrapper">
    <Sidebar @moduleID="appendEmialComponent" :moduleConfig="moduleConfig" :modules="emailComponents"/>

    <section id="email-body">
      <html lang="en" xmlns="http://www.w3.org/1999/xhtml" xmlns:v="urn:schemas-microsoft-com:vml"
        xmlns:o="urn:schemas-microsoft-com:office:office">

      <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="x-apple-disable-message-reformatting">
        <title></title>
      </head>

      <body width="100%"
        style="margin: 0; padding: 0 !important; mso-line-height-rule: exactly; background-color: #222222;">
        <center style="width: 100%; background-color: #ffffff;">
          
          <Preheder v-if="emailConfig.preheder"/>

          <table align="center" role="presentation" cellspacing="0" cellpadding="0" border="0" :width="emailConfig.width" style="margin: auto;" class="email-container">
            <component v-for="(component, index) in emailBody" :is="component" :key="index" :id="index" @removeModule="handelRemoveModule" @emitModuleConfig="handelConfig"/>
          </table>

        </center>
      </body>

      </html>
    </section>

  </section>
</template>

<script>
import Sidebar from '@/components/sidebar/Sidebar'

import Preheder from '@/components/email/Preheder'
import Header from '@/components/email/Header'
import HeroImage from '@/components/email/HeroImage'
import OneColumnTextPlusButton from '@/components/email/OneColumnTextPlusButton'
import BackgroundImageWithText from '@/components/email/BackgroundImageWithText'
import TwoEvenColumns from '@/components/email/TwoEvenColumns'
import ThreeEvenColumns from '@/components/email/ThreeEvenColumns'
import ThumbnailLeftTextRight from '@/components/email/ThumbnailLeftTextRight'
import ThumbnailRightTextLeft from '@/components/email/ThumbnailRightTextLeft'
import ClearSpacer from '@/components/email/ClearSpacer'
import OneColumnText from '@/components/email/OneColumnText'
import Footer from '@/components/email/Footer'

export default {
  components: {
    Sidebar, Preheder, Header, HeroImage, OneColumnTextPlusButton, BackgroundImageWithText, TwoEvenColumns, ThreeEvenColumns, ThumbnailLeftTextRight, ThumbnailRightTextLeft, ClearSpacer, OneColumnText, Footer,
  },
  data () {
    return {
      moduleConfig: {},
      emailConfig: {
        preheder: false,
        width: 640,
      },
      emailComponents: ['Preheder', 'Header', 'HeroImage', 'OneColumnTextPlusButton', 'BackgroundImageWithText', 'TwoEvenColumns', 'ThreeEvenColumns', 'ThumbnailLeftTextRight', 'ThumbnailRightTextLeft', 'ClearSpacer', 'OneColumnText', 'Footer'],
      emailBody: []
    }
  },
  methods: {
    appendEmialComponent (id) {
      if (id === 0) this.emailConfig.preheder = !this.emailConfig.preheder
      else this.emailBody.push(this.emailComponents[id])
    },
    handelRemoveModule (id) {
      this.emailBody = this.emailBody.filter((value, index) => index !== id);
    },
    handelConfig (moduleConfig = {}) {
      this.moduleConfig = moduleConfig
    }
  }
  /*
    TODO:
    Preheder
    Header
    HeroImage
    BackgroundImageWithText
    ClearSpacer
    Footer

    DONE:
    OneColumnTextPlusButton
    TwoEvenColumns
    ThreeEvenColumns
    ThumbnailLeftTextRight
    ThumbnailRightTextLeft
    OneColumnText
  */
}
</script>

<style>
  .main-wrapper {
    display: flex;
    flex-wrap: nowrap;
  }

  #email-body { 
    display: block;
    max-width: 640px;
    margin: 0 100px 0 auto;
  }
</style>
