<template>
  <main class="v-mail-signature-generator fp-page">
    <div class="fp-grid-coll-container fp-grid-coll-container--center">
      <div class="fp-grid-coll-24-24 fp-grid-coll-reg-12-24 fp-grid-with-gutter">
        <h1>Générateur de&nbsp;signature mail le cinematographe</h1>

        <form
            class="v-mail-signature-generator__content fp-ui-form"
        >
          <input type="text" placeholder="prénom"   v-model="firstname">
          <input type="text" placeholder="nom"      v-model="name">
          <input type="text" placeholder="pronom"      v-model="pronom">
          <input type="text" placeholder="fonction" v-model="activity" >
          <input type="text" placeholder="numéro"   v-model="tel" >
        </form>

        <div
            @click="copySignatureInClipBoard"
            class="v-mail-signature-generator__container"
        >
          <div
              dir="ltr"
              ref="htmlContent"
              style="width: 100%"
          >
            <table cellpadding="0" cellspacing="0" border="0" role="presentation"
                   style="border-collapse: collapse !important; width: auto;">
              <tr>
                <td style="vertical-align: top;">
                  <table cellpadding="0" cellspacing="0" border="0" role="presentation">
                    <tr>
                      <td style="vertical-align: top;padding-right: 0px; border-right: 2px dotted #000; padding-bottom: 30px; padding-top: 30px;">
                        <p style="text-align: center; margin: 0">
                          <img
                                alt="logo lecinematographe"
                                height="151"
                                style="height: 151px"
                                src="https://villa1203.github.io/lecinematographe.signature/logo.png"
                          />
                        </p>
                      </td>
                      <td style="padding-right: 15px; "></td>
                    </tr>
                  </table>
                </td>
                <td style="vertical-align: top;">
                  <p style="font-family:Helvetica, Arial, sans-serif; color: #444444; padding: 0; margin: 0; font-size: 20px; font-weight: bold;"
                  >
                    {{getCleanedEmptyString(firstname, 'prénom')}} {{getCleanedEmptyString(name, '/ nom')}}
                    <br><span style="font-size: 12px; font-family:Helvetica, Arial, sans-serif;">({{getCleanedEmptyString(pronom, 'pronom')}})</span>
                  </p>

                  <table width="100%" border="0" cellspacing="0" cellpadding="0">
                    <tr>
                      <td style="line-height: 10px">&nbsp;</td>
                    </tr>
                    <tr>
                      <td style="border: none; line-height: 1px; height: 1px; background-color: #eeeeee;"></td>
                    </tr>
                    <tr>
                      <td style="line-height: 10px">&nbsp;</td>
                    </tr>
                  </table>

                  <p style="font-family:Helvetica, Arial, sans-serif; color: #444444; padding: 0; margin: 0; font-size: 12px; line-height: 15px;"
                  >
                    {{getCleanedEmptyString(activity, 'fonction')}}
                    <br>
                    <br>
                  </p>

                  <p style="font-family:Helvetica, Arial, sans-serif; color: #444444; padding: 0; margin: 0; font-size: 12px; line-height: 15px;"
                  >
                    Le Cinématographe
                    <br>
                  </p>

                  <p style="font-family:Helvetica, Arial, sans-serif; color: #444444; padding: 0; margin: 0; font-size: 12px; line-height: 15px;"
                  >
                    Casino de Montbenon,
                    <br>All. Ernest-Ansermet 3,
                    <br>1003 Lausanne
                    <br>
                  </p>

                  <p style="font-family:Helvetica, Arial, sans-serif; color: #444444; padding: 0; margin: 0; font-size: 12px; line-height: 15px;"
                  >
                    <a :href="'tel:' + tel"
                       target="_blank"
                       style="color: #444444"
                    >
                       {{getCleanedEmptyString(tel, 'numéro')}}
                    </a>
                  </p>

                  <p style="font-family:Helvetica, Arial, sans-serif; color: #444444; padding: 0; margin: 0; font-size: 12px; line-height: 15px;">
                    <a id="websiteLink"
                       target="_blank"
                       style="color: #444444; text-decoration: underline;"
                       href="https://lecinematographe.ch/"
                    >lecinematographe.ch</a></p>
                  <p style="padding: 0;margin: 0; text-align: left; font-size: 12px; line-height: 15px; font-weight: normal;">
                    <a href="https://www.instagram.com/lecinematographe_lausanne/"
                       style="color: #444444; text-decoration: underline;"
                       target="_blank"
                    >
                      @lecinematographe_lausanne
                    </a>
                  </p>
                </td>
              </tr>
            </table>
          </div>
        </div>
        <button
            @click="copySignatureInClipBoard"
            class="fc-button"
        >Selectionner le texte de signature</button>

          <p
                  style="padding-top: 1rem"
                  class="fp-text-small" >
              Une fois le texte sélectionné (le texte devient vert quand il est sélectionné), copiez-le et collez-le dans votre
              outil de messagerie mail, dans les paramètres de signatures automatiques.
          </p>

        <div class="v-mail-signature-generator__code-viewer"
        >
          <button @click="showCode = !showCode"
                  class="fc-button--small"
                  style="
                    background: black;
                    margin-bottom: 1rem;
                  "
          >voir le code</button>

          <textarea style="font-size: 12px; line-height: 14px"
                    readonly
                    v-if="showCode"
          >
            <table cellpadding="0" cellspacing="0" border="0" role="presentation"
                   style="border-collapse: collapse !important; width: auto;">
              <tr>
                <td style="vertical-align: top;">
                  <table cellpadding="0" cellspacing="0" border="0" role="presentation">
                    <tr>
                      <td style="vertical-align: top;padding-right: 0px; border-right: 2px dotted #000; padding-bottom: 30px; padding-top: 30px;">
                        <p style="text-align: center; margin: 0">
                          <img
                                alt="logo lecinematographe"
                                height="151"
                                style="height: 151px"
                                src="https://villa1203.github.io/lecinematographe.signature/logo.png"
                          />
                        </p>
                      </td>
                      <td style="padding-right: 15px; "></td>
                    </tr>
                  </table>
                </td>
                <td style="vertical-align: top;">
                  <p style="font-family:Helvetica, Arial, sans-serif; color: #444444; padding: 0; margin: 0; font-size: 20px; font-weight: bold;"
                  >
                    {{getCleanedEmptyString(firstname, 'prénom')}} {{getCleanedEmptyString(name, '/ nom')}}
                    <br><span style="font-size: 12px; font-family:Helvetica, Arial, sans-serif;">({{getCleanedEmptyString(pronom, 'pronom')}})</span>
                  </p>

                  <table width="100%" border="0" cellspacing="0" cellpadding="0">
                    <tr>
                      <td style="line-height: 10px">&nbsp;</td>
                    </tr>
                    <tr>
                      <td style="border: none; line-height: 1px; height: 1px; background-color: #eeeeee;"></td>
                    </tr>
                    <tr>
                      <td style="line-height: 10px">&nbsp;</td>
                    </tr>
                  </table>

                  <p style="font-family:Helvetica, Arial, sans-serif; color: #444444; padding: 0; margin: 0; font-size: 12px; line-height: 15px;"
                  >
                    {{getCleanedEmptyString(activity, 'fonction')}}
                    <br>
                    <br>
                  </p>

                  <p style="font-family:Helvetica, Arial, sans-serif; color: #444444; padding: 0; margin: 0; font-size: 12px; line-height: 15px;"
                  >
                    Le Cinématographe
                    <br>
                  </p>

                  <p style="font-family:Helvetica, Arial, sans-serif; color: #444444; padding: 0; margin: 0; font-size: 12px; line-height: 15px;"
                  >
                    Casino de Montbenon,
                    <br>All. Ernest-Ansermet 3,
                    <br>1003 Lausanne
                    <br>
                  </p>

                  <p style="font-family:Helvetica, Arial, sans-serif; color: #444444; padding: 0; margin: 0; font-size: 12px; line-height: 15px;"
                  >
                    <a :href="'tel:' + tel"
                       target="_blank"
                       style="color: #444444"
                    >
                       {{getCleanedEmptyString(tel, 'numéro')}}
                    </a>
                  </p>

                  <p style="font-family:Helvetica, Arial, sans-serif; color: #444444; padding: 0; margin: 0; font-size: 12px; line-height: 15px;">
                    <a id="websiteLink"
                       target="_blank"
                       style="color: #444444; text-decoration: underline;"
                       href="https://lecinematographe.ch/"
                    >lecinematographe.ch</a></p>
                  <p style="padding: 0;margin: 0; text-align: left; font-size: 12px; line-height: 15px; font-weight: normal;">
                    <a href="https://www.instagram.com/lecinematographe_lausanne/"
                       style="color: #444444; text-decoration: underline;"
                       target="_blank"
                    >
                      @lecinematographe_lausanne
                    </a>
                  </p>
                </td>
              </tr>
            </table>
          </textarea>
        </div>

      </div>

    </div>
  </main>
</template>

<script lang="ts">
import {defineComponent} from "vue"

export default defineComponent({

  data() {
    return {
      firstname: '',
      name: '',
      activity: '',
      tel: '',
      pronom: '',
      showCode: false,
    }
  },

    methods: {
    copySignatureInClipBoard() {
      /* Get the text field */
      const htmlContentToCopy = this.$refs.htmlContent;

      if(!( htmlContentToCopy instanceof HTMLElement)) return

      const selection = window.getSelection()
      const range = document.createRange()

      range.selectNodeContents(htmlContentToCopy)

      if(! selection) return
      selection.removeAllRanges()
      selection.addRange(range)

      // todo: other methode to implement
      // function setClipboard(text) {
      //   const type = "text/html";
      //   const blob = new Blob(['<h1>'+text+'</h1>'], { type });
      //   const data = [new ClipboardItem({ [type]: blob })];
      //
      //   navigator.clipboard.write(data).then(
      //       function () {
      //         /* success */
      //         console.log('succcess')
      //       },
      //       function (e) {
      //         /* failure */
      //         console.log('failed')
      //         console.log(e)
      //       }
      //   );
      // }

    },

    getCleanedEmptyString(value: string, placeholder: string):string {
      if(value.length > 0) return value
      return placeholder + ' doit être rempli'
    }
  },

})</script>

<style lang="scss" scoped>

h1 {
  font-size: 3rem;
  line-height: 1em;
}

.v-mail-signature-generator {
  min-height: calc(100vh - 200px);
  padding-bottom: 1rem;

  *::selection {
    background-color: #83FFA0FF;
  }
}

.v-mail-signature-generator__container {
  padding: 1rem;
  margin-bottom: 1rem;
  background: white;

  > table {
    pointer-events: none;
  }

}

.fp-ui-form {
  display: flex;
  flex-wrap: wrap;

  > input {
    all: unset;
    display: block;
    position: relative;
    width: 100%;
    cursor: pointer;
    box-sizing: border-box;
    background: var(--color-background);
    box-shadow: inset 0 0 0 2px currentColor;
    margin-bottom: 1rem;
    line-height: .5ex;
    padding: .5rem 1rem;
  }
}

.v-mail-signature-generator__code-viewer {
  padding: 2rem 0;
  display: flex;
  align-items: center;
  flex-direction: column;

  textarea {
    display: block;
    width: 100%;
    height: 20rem;
    resize: none;
  }
}
</style>
