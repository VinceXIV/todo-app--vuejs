### 1. **How long did you spend on the coding test? What would you add to your solution if you had more time? If you didn't spend much time on the coding test then use this as an opportunity to explain what you would add.**
I spent about 2 - 3. One interesting thing is that I had long times in between the times I was working on it because of other commitments. That, to some extent, was a challenge because I had to reread my code, and the commit messages to figure out where I left it so I could continue building on it.

If I had more time, I would improve the structure of my code on areas that I'll mention shortly. Also, I didn't make the todos draggable, so that is another thing I would do

### 2. **Which parts did you spend the most time with? What did you find most difficult?**
There is this thing I was trying. I felt like there was - there should be a way to require files conditionally. Here's how my code for the part I was loading images looks like now. It works, but **I don't like the way it is structured**.

```
<template>
  <div class="container" :class="[theme, mode]">
    <img :src="imageDesktopDark" class="desktop dark" alt="Mountain">
    <img :src="imageDesktopLight" class="desktop light" alt="Mountain">
    <img :src="imageMobileDark" class="mobile dark" alt="Mountain">
    <img :src="imageMobileLight" class="mobile light" alt="Mountain">
    <div id="bottom-div" :class="theme"></div>
    <p :class="[theme, mode]">Drag and drop to reorder list</p>
  </div>
</template>

<script>
export default {
  name: 'BackGround',
  props: {
    theme: String,
    mode: String
  },

  data() {
    return {
      imageDesktopDark: require(`../assets/images/bg-desktop-dark.jpg`),
      imageDesktopLight: require(`../assets/images/bg-desktop-light.jpg`),
      imageMobileDark: require(`../assets/images/bg-mobile-dark.jpg`),
      imageMobileLight: require(`../assets/images/bg-mobile-light.jpg`)
    }
  }
}
</script>
```

As can be seen, there's a lot of repitition going on. For one, I have used four links for image, each taking care of a particular theme and mode. Only one of the images corresponding to the current theme and mode set by a user is used. Others are set to `display: none;` in the css file. I wanted to only use one `img` tag and use only one image url data to make the code cleaner. I figured I could make the data that gets returned to be in the form; `../assets/images/bg-${mode}-${theme}.jpg` and/or maybe I could use `reactive` or `ref` in the process. That way, I would write something close to this;

 ```
 data() {
    image: require(`../assets/images/bg-${mode}-${theme}.jpg`)
 }
 ```
 
 I would also need only one `img` tag thereby relieving me of the need to `display: none;` some items. the code would have been cleaner that way. Problem is, I couldn't quickly figure a way to achieve that in the short period I was working on the code.
 
 There are a couple more of my implementations that I felt like they needed some improvement including the todo tasks data. I made two arrays, one that gets passed down and shows what todo is to be displayed, and other that keeps the whole todo list items so that even if we only display the active ones, we still have the whole list and can display it whenever we like. I could have implemented this without the use of two arrays as that is not exactly healthy on space. That said, it is a todo app and the items are "guaranteed" to only be a few, so the concern could be ignored

 Another thing is that I couldn't find the font Rubik sans. I tried Rubik in itself but the font didn't look like the ones on the screenshots. I had to look for one that matched the one on the screenshots

### 3. **What was the most useful feature that was added to the latest version of Vue.js? Please include a snippet of code that shows how you've used it.**
There were a lot of features that were added to Vue-3 including enabling the use of multiple v-models and multiple root elements. I've used a couple of them.
#### - _using a multiple v-models_
As opposed to Vue-2 that only allows the use of 1 v-model on a component, Vue-3 allows more. Here are examples of me taking advantage of this;
```
<TodoListItem
    v-for="task in todoTasks"
    :key="task.id"
    :task="task"
    :theme="theme"
    :mode="mode"
    @toggle-todo-state="onToggleTodoState"
    @remove-todo-item="onRemoveTodoItem"
/>
```

#### - _Multiple root elements_
In Vue-2, only one root elements was allowed. This forced one to use add wrap everything in a div whenever they wanted a template that has a couple of items inside them. Vue-3 solved this gracefully. Here's me taking advantage of this
```
<template>
  <BackGround :theme="theme" :mode="mode"/>
  <ToDo :theme="theme" :mode="mode" @toggleTheme="toggleTheme"/>
</template>
```

#### - _Better management of third party plugins through global mounting_
Using Vue-3 means one nolonger needs to use the the troublesome Global Vue instance when installing plugins and other libraries. In my case, I haven't used third party plugins but I've created the app in accordance with expectations in Vue-3. Here my main.js looks like;
```
import { createApp } from 'vue'
import App from './App.vue'

createApp(App).mount('#app')
```

If I need to add new plugins, then I can add them as follows;
```
import { createApp } from 'vue'
import App from './App.vue'
const myApp = createApp(App)

myApp.use(/* the name of the plugin I would like to use*/)
myApp.use(/* another plugin*/)

myApp.mount('#app')
```

The advantage of global mounting is the application would be protected from unwanted/unexpected changes to global instance made by plugins/libraries made by, for instance, using Mixins
### 4. **How would you track down a performance issue in production? Have you ever had to do this?**
The first thing I usually do is check how the app behaves generally. Is it slow in certain instances, but not others, or is it generally slower than I expect it to be? I also test a few scenarios to ensure it works as expected. I did this with this test program too and that's how I identified issues such as the fact that when I removed all items in the todo list, adding new items resulted in an unexpected behavior of the app. I found that for the new ones, clicking on one resulted in marking all items as "completed", which was due to all of them having an id of "undefined".

Another thing I usually do is check how resources are being used and released. For instance, I expect certain resources (such as memory, stuff saved on local storage, and cached) to be released once certain processes have been completed. There was a time I had my app misbehaving because of caching issue - the browser wasn't allowing caching because the front end and the backend were deployed from different domains. I found this problem by checking how the resources are being used and figured while caching was as expected when the app was run locally, it was failing when deployed

I also try to run the same application in different environments, sometimmes changing a few things. That's especially the case when I find out that the app works on one environment but not another. As such, I try to understand why it works in one environment but not another.

### 5. **How did you find the test overall? Did you have any issues or have difficulties completing? If you have any suggestions on how we can improve the test, we'd love to hear them.**
I found the test interesting. One thing I noticed is that it had a lot of "minute" details that required a keen eye. I was actually hesitant of submitting my work because it felt like there's something deep in the details that I was missing. For one, I noticed the caret-cursor was not white-ish (the default since the text was set to white-ish). I had to go back and change that. There's also how the way the cross on each todo item was not consistent in desktop, and mobile modes. For smaller screen size (mobile mode), the crosses were on each todo regardless of whether or not they had been marked as completed. It wasn't exactly the same in desktop version where it appeared when hovering on a todo item.

I don't have much of a suggestion on ways to improve the tests. If I said anything, it would probably be in the line of "Keep up on what you're doing, especially on the minute details". It was very easy to miss the details. I still feel like I have missed a few, so I'll have to go back and check even after submitting this.

Thanks.