
<p align="center">
  <img src="vue-axe.svg" alt="Vue Axe logo">
</p>

## [@vue-a11y/axe](https://github.com/vue-a11y/vue-axe)
Accessibility auditing for Vue.js 3 applications by running [dequelabs/axe-core](https://github.com/dequelabs/axe-core/) validation on the page you're viewing.

- [Links](#links)
- [Setup](#setup)
- [Options](#options)
- [Locales](#locales)

## Links
- [Demo](https://vue-axe-next.surge.sh/)

## Setup
```shell
npm install -D axe-core vue-axe@next
# or
yarn add -D axe-core vue-axe@next
```

### Vue CLI
```js
import { createApp, h } from 'vue'
import App from './App.vue'

let app = null

if (process.env.NODE_ENV === 'development') {
  const VueAxe = require('vue-axe')
  app = createApp({
    render: () => h('div', {}, [h(App), h(VueAxe.VueAxePopup)])
  })
  app.use(VueAxe.default)
} else {
  app = createApp(App)
}

app.mount('#app')
```

## Options

### auto

| Type     | Default  |
| -------- | -------- |
| Boolean  | `true`   | 

If false disables automatic verification. 
It is necessary to click on `run again` for a new analysis.

### config

| Type     | Default                                  |
| -------- | ---------------------------------------- |
| Object   | `{ branding: { application: 'vue-axe' }` | 

To configure the format of the data used by axe.  
This can be used to add new rules, which must be registered with the library to execute.

NOTE: Learn more about [Axe-core configuration](https://github.com/dequelabs/axe-core/blob/master/doc/API.md#api-name-axeconfigure)

### runOptions

| Type     | Default                                                         |
| -------- | --------------------------------------------------------------- |
| Object   | `{ runOptions: { reporter: 'v2', resultTypes: ['violations'] }` | 

Flexible way to configure how `axeCore.run()` operates.

NOTE: Learn more about [Axe-core runtime options](https://github.com/dequelabs/axe-core/blob/master/doc/API.md#options-parameter)

### plugins

| Type     |
| -------- |
| Array    | 

Register Axe plugins.

```js
const plugins = require('@/plugins/axe')
app.use(VueAxe, {
  plugins: [plugins.myPlugin, plugins.myPlugin2]
})
```

## Locales

Through the settings it is possible to define the language that will be used for the violations.

NOTE: axe-core already has several languages ​​available.  
[See axe-core locales](https://github.com/dequelabs/axe-core/tree/develop/locales)

```js
const ptBR = require('axe-core/locales/pt_BR.json')
app.use(VueAxe, {
  config: {
    locale: ptBR
  }
})
```

## Contributing
- From typos in documentation to coding new features;
- Check the open issues or open a new issue to start a discussion around your feature idea or the bug you found;
- Fork repository, make changes and send a pull request;

Follow us on Twitter [@vue_a11y](https://twitter.com/vue_a11y)

**Thank you**







