<template>
  <div class="grid place-items-center">
    <h2 class="my-5 text-xl font-bold">Caesar Cipher</h2>
    <label for="input" class="my-5 mr-2 font-bold"
      >Type Message to Encrypt</label
    >
    <textarea
      class="block w-1/2 border-2 border-gray-400 rounded h-36"
      name="input"
      v-model="msg"
    />
    <div class="grid block w-1/2 my-5 place-items-center">
      <h1 class="my-2 font-bold">Encrypted Message</h1>
      <textarea
      class="block w-full border-2 border-gray-400 rounded h-36"
      name="input"
      v-model="encryptedMessage"
    />
      <button class="p-2 my-5 border-2 border-gray-100 rounded-lg hover:bg-teal-200" @click="copy">
        <span class="material-icons">content_copy</span>
      </button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "@vue/runtime-core";

export default defineComponent({
  data() {
    return {
      msg: "",
      shift: 3,
    };
  },
  methods: {
    copy() {
        (this.$refs.encrypted as any).focus();
        document.execCommand('copy');
        (this.$refs.encrypted as any).blur();
    },
    wrapRange(code: number){
        if (code > 90) return 65 + code%91;
        else return code;
    },
    // selectMsg(){
    //     (this.$event.target as HTMLInputElement).select();
    // }
  },
  computed: {
    encryptedMessage(): string {
      let e = "";
      for (let i = 0; i < this.msg.length; i++) {
        let code: number = this.msg.toUpperCase().charCodeAt(i);
        e +=
          code >= 65 && code <= 90
            ? String.fromCharCode(this.wrapRange(code + this.shift))
            : this.msg.charAt(i);
        // e += code;
      }
      return e;
    },
  },
});
</script>

<style lang="scss" scoped>
</style>