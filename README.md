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
