<template>
<div class="container mx-auto">
    <!-- <div class="border m-6 rounded-lg  bg-white mx-auto max-w-sm shadow-lg rounded-lg overflow-hidden"> -->
      <form class="w-full max-w-md">
        <div class="flex flex-wrap -mx-3 mb-6">
          <div class="w-full px-3">
            <label class="block uppercase tracking-wide text-grey-darker text-xs font-bold mb-2" for="grid-password">
              Name
            </label>
            <input class="appearance-none block w-full bg-grey-lighter text-grey-darker border border-grey-lighter rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white focus:border-grey" id="grid-password" v-model="signature" type="text" @keyup.enter="createSignature" placeholder="John Albanese">
            <p class="text-grey-dark text-xs italic">Press Enter key to generate signature</p>
          </div>
        </div>
        <div class="flex flex-wrap -mx-3 mb-2">
          <div class="w-full  px-3 mb-6 md:mb-0">
            <label class="block uppercase tracking-wide text-grey-darker text-xs font-bold mb-2" for="grid-city">
              Font Size
            </label>
            <input class="appearance-none block w-full bg-grey-lighter text-grey-darker border border-grey-lighter rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-grey" id="grid-city" type="text" placeholder="Albuquerque">
          </div>
          <div class="w-full  px-3 mb-6 md:mb-0">
            <label class="block uppercase tracking-wide text-grey-darker text-xs font-bold mb-2" for="grid-city">
              Font Family
            </label>
            <input class="appearance-none block w-full bg-grey-lighter text-grey-darker border border-grey-lighter rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-grey" id="grid-city" type="text" placeholder="Albuquerque">
          </div>
          <div class="w-full  px-3 mb-6 md:mb-0">
            <label class="block uppercase tracking-wide text-grey-darker text-xs font-bold mb-2" for="grid-state">
              Font Url
            </label>
            <div class="relative">
              <input class="appearance-none block w-full bg-grey-lighter text-grey-darker border border-grey-lighter rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-grey" id="grid-city" type="text" placeholder="Albuquerque">
              <div class="pointer-events-none absolute pin-y pin-r flex items-center px-2 text-grey-darker">
              </div>
            </div>
          </div>
          <div class="w-full  px-3 mb-6 md:mb-0">
            <label class="block uppercase tracking-wide text-grey-darker text-xs font-bold mb-2" for="grid-zip">
              Font Color
            </label>
            <input class="appearance-none block w-full bg-grey-lighter text-grey-darker border border-grey-lighter rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-grey" id="grid-zip" type="text" placeholder="90210">
          </div>
        </div>
        <div class="flex flex-wrap -mx-3 mb-2">
          <div class="w-full  px-3 mb-6 md:mb-0">
            <label class="block uppercase tracking-wide text-grey-darker text-xs font-bold mb-2" for="grid-city">
              Image Height[px]
            </label>
            <input class="appearance-none block w-full bg-grey-lighter text-grey-darker border border-grey-lighter rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-grey" id="grid-city" type="text" placeholder="Albuquerque">
          </div>
          <div class="w-full  px-3 mb-6 md:mb-0">
            <label class="block uppercase tracking-wide text-grey-darker text-xs font-bold mb-2" for="grid-city">
              Image Width[px]
            </label>
            <input class="appearance-none block w-full bg-grey-lighter text-grey-darker border border-grey-lighter rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-grey" id="grid-city" type="text" placeholder="Albuquerque">
          </div>
          <div class="w-full  px-3 mb-6 md:mb-0">
            <label class="block uppercase tracking-wide text-grey-darker text-xs font-bold mb-2" for="grid-state">
              Image Padding X
            </label>
            <div class="relative">
              <input class="appearance-none block w-full bg-grey-lighter text-grey-darker border border-grey-lighter rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-grey" id="grid-city" type="text" placeholder="Albuquerque">
              <div class="pointer-events-none absolute pin-y pin-r flex items-center px-2 text-grey-darker">
              </div>
            </div>
          </div>
          <div class="w-full  px-3 mb-6 md:mb-0">
            <label class="block uppercase tracking-wide text-grey-darker text-xs font-bold mb-2" for="grid-zip">
              Image Padding Y
            </label>
            <input class="appearance-none block w-full bg-grey-lighter text-grey-darker border border-grey-lighter rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-grey" id="grid-zip" type="text" placeholder="90210">
          </div>
        </div>
      </form>
      <img :src="image" />
    <!-- </div> -->
</div>
      <!-- <input type="text" v-model="signature" @keyup.enter="createSignature" />
      <small>Press enter to change signature</small>
   -->
</template>

<script>
import TextSignature  from 'text-signature';
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      image: '',
      signature: 'John Albanese',
      signature_options: {
        width: 700,
        height: 300,
        paddingX: 100,
        paddingY: 100,
        canvasTargetDom: ".js-canvasTargetDom",
        font:  ["50px", "'Homemade Apple'"],
        color: "blue",
        textString: "John Albanese",
        customFont: { 
          name: "'Homemade Apple'", 
          url: "http://fonts.googleapis.com/css?family=Homemade+Apple"  
        }
      }
    }

  },
  methods: {
    createSignature() {
      this.signature_options.textString = this.signature;
      let sign = new TextSignature(this.signature_options);
      sign.generateImage(this.signature_options);
      this.image = sign.getImageData();
    }
  },
  mounted(){
    let sign = new TextSignature(this.signature_options);
    sign.generateImage(this.signature_options);
    this.image = sign.getImageData();
  },
}
</script>
