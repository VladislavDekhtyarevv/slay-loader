# Slay Loader library for Vue3

GitHub repository: <a target="_blank" href="https://github.com/VladislavDekhtyarevv/slay-loader" >Slay loader</a>

Here's a brief  introduction or check <a href="https://vladislavdekhtyarevv.github.io/slay-loader/" >documentation</a>

You can use it with global state your app, and connect the component on main App file.
Or you can use it on separate page, and change state loader from local data.

### What does it look like
<p align="center">
    <img src="https://github.com/VladislavDekhtyarevv/slay-loader/blob/main/example.png" width="800px">
    <br>
</p>

### Installation

$ npm i slay-loader

### Use

--------
main.ts
```
import { createApp } from 'vue';
import App from './App.vue';
import { SlayLoader } from 'slay-loader';
import 'slay-loader/dist/style.css';
createApp(App)
    .component('SlayLoader', SlayLoader)
    .mount('#app')
```

-----

------
Component
```
<SlayLoader
      :show="true"
      :animation="`fade`"
      :time="500"
      :background="`radial-gradient(circle, rgba(198,90,254,1) 0%, rgba(184,251,196,1) 100%)`"
      :text="`Please wait, loading...`"
  />
```
------

### Options
Directive | Type | Description
--- | --- | ---
show | boolean | Show or hide loader
animation | string | Visual effect animation (fade, drag-top, drag-bottom, drag-left, drag-right)
time | number | Number duration animation in ms
background | string | Background color for loader (it can be gradient, or something else)
text | string | Text on loader
spinner | string | It can be your custom image spinner (examole: `/assets/puff.svg`)
