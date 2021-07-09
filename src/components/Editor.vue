<template>
  <v-container>
    <codemirror class="ma-10" v-model="code" :options="cmOptions"></codemirror>
    <pre id="output"></pre>
    <canvas id="mycanvas"></canvas>
    <v-btn v-on:click="runit()">Run</v-btn>
  </v-container>
</template>

<script>
import { codemirror } from "vue-codemirror";
import { Sk } from "skulpt";
import "codemirror/lib/codemirror.css";
// language
import "codemirror/mode/javascript/javascript.js";

// theme css
import "codemirror/theme/paraiso-light.css";

// require active-line.js
import "codemirror/addon/selection/active-line.js";

export default {
  name: "Editor",
  components: {
    codemirror,
  },
  data() {
    return {
      code: "const a = 10",
      cmOptions: {
        tabSize: 4,
        styleActiveLine: true,
        lineNumbers: true,
        line: true,
        mode: "text/javascript",
        theme: "paraiso-light",
      },
    };
  },
  methods: {
    // outf(text) {
    //   var mypre = document.getElementById("output");
    //   mypre.innerHTML = mypre.innerHTML + text;
    // },

    // builtinRead(x) {
    //   if (
    //     Sk.builtinFiles === undefined ||
    //     Sk.builtinFiles["files"][x] === undefined
    //   )
    //     throw "File not found: '" + x + "'";
    //   return Sk.builtinFiles["files"][x];
    // },
teste() {console.log('teste')},
    runit() {
      var prog = 'oi';
      var mypre = document.getElementById("output");
      mypre.innerHTML = "";
      Sk.pre("output")
      
      Sk.configure({ output: 'nada', read: 'nada' });
      (Sk.TurtleGraphics || (Sk.TurtleGraphics = {})).target = "mycanvas";
      var myPromise = Sk.misceval.asyncToPromise(function () {
        return Sk.importMainWithBody("<stdin>", false, prog, true);
      });
      myPromise.then(
       console.log('oiiiii')
      );
    },
  },
};
</script>