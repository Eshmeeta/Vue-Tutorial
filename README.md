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

#Reactivity
Reactivity in Vue.js ensures that your web page stays in sync with the data changes automatically, without you having to manually update the HTML.


