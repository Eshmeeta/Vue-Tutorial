# Vue-Tutorial

# Vue Project Setup
1. Create a new folder.
2. Open cmd.
3. Type the command - vue create learning(project name)
4. Select the Vue version. Then type : cd learning.
5. To open in VS Code; type code .

# Structure of a Vue file
Every Vue file contains 3 blocks :
1. Template - analogous to HTML.
2. Script - Analogous to JS
3. Style - Analogous to CSS


## Binding Text
1. Text Interpolation - using {}
2. v-text {drawback : replaces the entire quantity inside the div element with data property value}

## Binding HTML
Use v-html directive

## Binding to Attributes 
v-bind:id="dynamicId"

button v-bind:disabled="isDisabled">View Profile<

## Binding to Class
h2 v-bind:class="isCurrentEmployee ? 'currentemployee' : 'exemployee'">{{ isCurrentEmployee ? 'Current Employee' : 'Exemployee' }}</h2




# Reactivity
Reactivity in Vue.js ensures that your web page stays in sync with the data changes automatically, without you having to manually update the HTML.

Can be achived through ref and reactive
Use ref for single, simple values and reactive for complex data structures.
ref wraps a value in an object with a .value property, while reactive makes the entire object reactive without the need for .value.

## Deep and Shallow Reactivity

Deep reactivity means that Vue makes all nested properties within an object reactive. If any property, even if deeply nested, changes, Vue will track these changes and update the DOM accordingly.
Shallow reactivity means that Vue only makes the top-level properties of an object reactive. Nested objects are not made reactive. If you mutate a nested property, Vue will not automatically track these changes.

## Understanding Caveats with Reactivity in Vue.js

Arrays and Collections: When using ref in reactive arrays or collections, you still need .value to access the value.
Templates:
Top-level ref properties are automatically unwrapped in templates.
Nested ref properties need .value to access their value.
For text interpolation, ref values are automatically unwrapped.

## Script Setup
It enables automatic scope sharing.


# Computed Properties
It is used to make the template simple. A computed property automatically tracks its reactive dependencies. 

# Binding HTML Classes
We can bind :class to an array to apply a list of classes:


const activeClass = ref('active')
const errorClass = ref('text-danger')
template
<div :class="[activeClass, errorClass]"></div>

# Binding Inline Styles
:style supports binding to JavaScript object values - it corresponds to an HTML element's style property:

js
const activeColor = ref('red')
const fontSize = ref(30)
template
<div :style="{ color: activeColor, fontSize: fontSize + 'px' }"></div>

# Conditional Rendering
1. v-if
2. v-else
3. v-if-else
4. v-show: Toggles the display property of CSS.
5. v-for
   When v-if and v-for are both used on the same element, v-if will be evaluated first.

# List Rendering 

## v-for
It is a good practice to use key with v-for. Key value should be unique.
You can also add index.
It can be used with v-if and computed properties also (use of filter).

# Event Handling 

Event Handler - v-on or shortcut = @ 
2 types : 
Inline Event Handler.
Method Event Handler
## Inline Handler : 
<button @click: "count++">Increase</button>
 ## Calling methods in Inline Handler:
 <button @click="say('hello')">Say hello</button>
 ## Accessing Event Argument in Inline Handlers
   <button @click="warn('Personal Details Cannot be provided to external employees.',$event)">Request Contact Number</button>
## Event Modifiers
.stop
.prevent
.self
.capture
.once
.passive

## Key Modifiers
Key modifiers in Vue.js allow you to listen for specific keyboard keys when handling keyboard events. This way, your event handler only runs if a particular key is pressed.
 
# Form Binding
v-model : Helps in 2 way binding.
Use of v-model with text,checkboxes,radio,multiline text,etc

#  Watchers
Think of a watcher as someone who is always looking at a clock and telling you every time the hour changes so you can do something special, like ringing a bell. In Vue, watchers help you react to changes in your data by triggering functions when the data updates.


# Props 
Used to pass data from parent component to child component.

# Events 
Used to pass events from child to parent component.

## Event Validation 
<script setup>
const emit = defineEmits({
  // No validation
  click: null,

  // Validate submit event
  submit: ({ email, password }) => {
    if (email && password) {
      return true
    } else {
      console.warn('Invalid submit event payload!')
      return false
    }
  }
})

function submitForm(email, password) {
  emit('submit', { email, password })
}


</script>

# Component v-model 
Let's use a practical example to understand how defineModel() can be used in a real-world application. Suppose we have a simple form where users can input and update their name. We'll have a parent component that contains the form and a child component that handles the input field.

Child Component (NameInput.vue)
This component contains an input field for the user's name. It uses defineModel() to bind the input value to the parent component.

vue
Copy code
<template>
  <div>
    <label for="name">Name: </label>
    <input id="name" v-model="model.value" /> <!-- Bind the input to the model -->
  </div>
</template>

<script setup>
const model = defineModel() // Create a two-way binding model
</script>
Parent Component (UserProfile.vue)
This component uses the child component to get and update the user's name.

vue
Copy code
<template>
  <div>
    <h2>User Profile</h2>
    <NameInput v-model="userName" /> <!-- Bind parent data to the child component -->
    <p>Your name is: {{ userName }}</p> <!-- Display the user's name -->
  </div>
</template>

<script setup>
import { ref } from 'vue'
import NameInput from './NameInput.vue'

const userName = ref('') // Initialize the user's name
</script>
How It Works
Child Component (NameInput.vue):

Contains an input field bound to model.value created by defineModel().
When the user types in the input field, model.value updates.
Parent Component (UserProfile.vue):

Binds its userName data to the child component’s model using v-model.
Displays the user's name with Your name is: {{ userName }}.
What You See
The initial user name is empty.
When the user types their name into the input field in the NameInput child component, model.value updates.
The userName in the parent component also updates automatically because of the two-way binding.
The updated name is displayed in the parent component
