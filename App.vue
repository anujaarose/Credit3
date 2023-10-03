<template>
  <div>
    <!-- 1. Template Syntax -->
    <p>a. Text Interpolation: {{ message }}</p>
    <p>b. Raw HTML: <span v-html="rawHtml"></span></p>
    <p>c. Attribute Bindings: <div :id="dynamicId"></div></p>
    <p>d. JavaScript expressions inside syntax: {{ 2 + 3 }}</p>

    <!-- 2. Methods -->
    <button @click="sayHello">Say Hello</button>

    <!-- 3. Reactivity Fundamentals -->
    <p>Reactivity Fundamentals: {{ count }}</p>

    <!-- 4. Computed Properties -->
    <p>Computed Property: {{ computedValue }}</p>

    <!-- 5. Class and Style Bindings -->
    <div :class="classObject" :style="styleObject">Class and Style Bindings</div>

    <!-- 6. List Rendering -->
    <ul>
      <li v-for="item in items" :key="item.id">{{ item.text }}</li>
    </ul>

    <!-- 7. Event Handling: Listening to Events -->
    <button @click="handleClick">Click me</button>

    <!-- 8. Form Input Bindings -->
    <input type="text" v-model="inputValue" />
    <input type="checkbox" v-model="isChecked" />
    <input type="radio" v-model="selectedOption" value="option1" />
    <input type="radio" v-model="selectedOption" value="option2" />
    <select v-model="selectedValue">
      <option value="value1">Option 1</option>
      <option value="value2">Option 2</option>
    </select>
    <textarea v-model="textareaValue"></textarea>

    <!-- 9. Watchers -->
    <p>Watcher: {{ watchedValue }}</p>

    <!-- 10. Components -->
    <CustomComponent :propData="message" @customEvent="handleCustomEvent">
      <template #slotName="slotProps">
        Slot Content: {{ slotProps.slotValue }}
      </template>
    </CustomComponent>

    <!-- 11. Router -->
    <router-link to="/route">Go to Route</router-link>
    <router-view></router-view>
  </div>
</template>

<script>
import { ref, computed } from 'vue';

export default {
  data() {
    return {
      // 1. Template Syntax
      message: "Hello, Vue!",
      rawHtml: "<span style='color: red;'>This is raw HTML</span>",
      dynamicId: "dynamic-element",

      // 3. Reactivity Fundamentals
      count: ref(0),

      // 4. Computed Properties
      computedValue: computed(() => this.count.value * 2),

      // 5. Class and Style Bindings
      classObject: {
        active: true,
        'text-danger': false,
      },
      styleObject: {
        color: 'blue',
        fontSize: '16px',
      },

      // 6. List Rendering
      items: [
        { id: 1, text: 'Item 1' },
        { id: 2, text: 'Item 2' },
        { id: 3, text: 'Item 3' },
      ],

      // 8. Form Input Bindings
      inputValue: '',
      isChecked: false,
      selectedOption: 'option1',
      selectedValue: 'value1',
      textareaValue: '',

      // 9. Watchers
      watchedValue: 'initial value',
    };
  },
  methods: {
    // 2. Methods
    sayHello() {
      alert('Hello!');
    },

    // 7. Event Handling
    handleClick() {
      this.count.value++;
    },

    // 10. Components
    handleCustomEvent(data) {
      console.log('Custom Event:', data);
    },
  },
};
</script>

<style>
/* 1. Template Syntax */
p {
  font-size: 18px;
  margin-bottom: 10px;
}

span {
  color: red;
}

/* 2. Methods */
button {
  background-color: #007bff;
  color: #fff;
  padding: 10px 20px;
  border: none;
  cursor: pointer;
  margin: 10px 0;
}

/* 3. Reactivity Fundamentals */
p {
  color: #ff5722;
}

/* 4. Computed Properties */
p {
  color: #4caf50;
}

/* 5. Class and Style Bindings */
div.active {
  background-color: #4caf50;
  color: #fff;
}

/* 6. List Rendering */
li {
  list-style-type: none;
  padding: 5px 0;
}

/* 7. Event Handling */
button {
  background-color: #f44336;
}

/* 8. Form Input Bindings */
input[type="text"],
select,
textarea {
  width: 100%;
  padding: 10px;
  margin: 5px 0;
}

/* 9. Watchers */
p {
  color: #9c27b0;
}

/* 10. Components */
.custom-component {
  background-color: #ffeb3b;
  padding: 10px;
  border: 1px solid #ffeb3b;
  margin: 10px 0;
}

/* 11. Router */
router-link {
  text-decoration: none;
  color: #007bff;
  margin-right: 10px;
}

</style>
