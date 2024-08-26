### Projeto Modelo VUEJS + 
#### TailWind CSS + JSON-Server e Axios
#### Criando o projeto
npm create vue@latest app-01

cd app-01
npm install
npm run dev

#### Dependências
npm i json-server
npm i axios
||
npm i json-server axios

#### rodar o projeto
npm run dev

#### TailwindCSS Config / Install
https://tailwindcss.com/docs/guides/vite#vue

npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p

* tailwind.config.js
```
/** @type {import('tailwindcss').Config} */ <br>
export default { <br>
  content: [ <br>
    "./index.html", <br>
    "./src/**/*.{vue,js,ts,jsx,tsx}", <br>
  ], <br>
  theme: { <br>
    extend: {}, <br>
  }, <br>
  plugins: [], <br>
} <br>
```

#### Json API criar e configurar

* package.json
```
"scripts": { <br>
    "dev": "vite", <br>
    "api": "json-server --watch dados.json", <br>
    "build": "vite build", <br>
    "preview": "vite preview" <br>
},
```
#### link ref.
https://www.youtube.com/watch?v=JpWWecMpaNI

* Thiago Matos
https://www.youtube.com/watch?v=JpWWecMpaNI