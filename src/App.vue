
Agregando vue por NPM
Introducción
Iniciando
Editando package.json
Webpack config
Agregando .babelrc
Vue cli 3
#Agregando vue por NPM
#Introducción
Si estamos trabajando en proyecto , ya mas estructurado donde estemos ocupando , webpack , por ejemplo podríamos incluir Vue , dentro del proyecto para poder trabajar con el.

Sabiendo esto vamos a instalar un proyecto con npm desde 0 , para que veas como agregar vue de manera correcta y sin complicaciones 💪 .

Para comenzar crearemos una carpeta en el directorio donde deseemos trabajar.

#Iniciando
Agregamos el siguiente comando npm init -y

Si todo resulta bien , el anterior comando debería haber creado un archivo llamado package.json

#Editando package.json
Lo que debemos hacer es editar la sección de scripts(serve) y devDependencies

  {
    "name": "vueProyect",
    "version": "1.0.0",
    "description": "",
    "main": "index.js",
    "scripts": {
      "serve": "webpack-dev-server --mode development"
    },
    "keywords": [],
    "author": "",
    "license": "ISC",
    "devDependencies": {
      "@babel/core": "^7.11.6",
      "@babel/preset-env": "^7.11.5",
      "babel-loader": "^8.1.0",
      "css-loader": "^3.6.0",
      "html-webpack-plugin": "^4.4.1",
      "vue": "^2.6.12",
      "vue-loader": "^15.9.3",
      "vue-style-loader": "^4.1.2",
      "vue-template-compiler": "^2.6.12",
      "webpack": "^4.44.1",
      "webpack-cli": "^3.3.12",
      "webpack-dev-server": "^3.11.0"
      }
 }

#Instalando las dependencias agregadas
le damos a instalar con

npm install
#Webpack config
luego debemos crear el archivo webpack.config.js quedando de este modo


const VueLoaderPlugin = require('vue-loader/lib/plugin');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  entry: './src/index.js',
  module: {
    rules: [
      { test: /\.js$/, exclude: /node_modules/, loader: "babel-loader" },
      { test:/\.vue$/, use: 'vue-loader' },
      { test:/\.css$/, use: ['vue-style-loader' , 'css-loader']}
    ]
  },
  plugins: [
    new HtmlWebpackPlugin({
    template: './src/index.html'
    }),
      new VueLoaderPlugin( ),
    ]
};
#Agregando .babelrc
agregar el archivo sin extensiones .babelrc en la raiz de nuestro proyecto.

{
  "presets": ["@babel/preset-env"]
}
Luego creamos un archivo en la carpeta src llamada *App.vue

<template>
  <div id="app">
    {{ message }}
  </div>
</template>

<script>
  export default {
    data() {
      return {
        message: 'Hola en vue',
      };
    }
  }
</script>

<style scoped>
  #app {
    font-size: 25px;
    font-family: "Calibri", sans-serif;
    color: darkblue;
    background: lightblue;
  }
</style>