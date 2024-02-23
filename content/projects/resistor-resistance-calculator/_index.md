---
title : Resistor Resistance Calculator
date : 2024-02-23T17:20:45Z
draft : false
---

### Introduction
This is a tutorial to calculate the resistance of a resistor. 
When i work on any electronics project and forget what the resistance of the resistor im using is i end up having to look it up. I then thought that this would be a good quick project to do.

##### [GitHub](https://github.com/awaisamjad/electronics)

### Prerequisites
- Basic JavaScript and HTML
- Understanding of how to calculate the resistance of a resistor through their colour bands
  
### Technologies used
- Any JavaScript framework or Vanilla JS can be used but we will be using **Svelte**

### Setup
{{% steps %}}

### Step 1

Open your terminal/command prompt and navigate to where you want to create your project

### Step 2

Run the following command where _resistor-resistance-calculator_ is the name of the project

```bash
npm create svelte@latest resistor-resistance-calculator
```
### Step 3
Navigate into the directory and pen with your favourite code editor/IDE. I use VSCode

```bash
cd resistor-resistance-calculator
code .
```

{{% /steps %}}

### Project Structure
Your project structure should look something like this (depending on the options you chose)
{{< filetree/container >}}
  {{< filetree/folder name=".svelte-kit" state="closed" >}}
      {{< filetree/file name="favicon.png" >}}
  {{< /filetree/folder >}}

  {{< filetree/folder name="assets" state="closed" >}}
  {{< /filetree/folder >}}

  {{< filetree/folder name="node_modules" >}}
  {{< /filetree/folder >}}

  {{< filetree/folder name="src" >}}
    {{< filetree/file name="_index.md" >}}

    {{< filetree/folder name="lib" state="closed" >}}
      {{< filetree/file name="index.js" >}}
    {{< /filetree/folder >}}

    {{< filetree/folder name="routes" state="open" >}}
      {{< filetree/file name="+page.svelte" >}}
    {{< /filetree/folder >}}
    {{< filetree/file name="app.html" >}}
  {{< /filetree/folder >}}

  {{< filetree/folder name="static" state="closed" >}}
      {{< filetree/file name="favicon.png" >}}
  {{< /filetree/folder >}}

  {{< filetree/file name=".gitignore" >}}
  {{< filetree/file name=".npmrc" >}}
  {{< filetree/file name=".prettierignore" >}}
  {{< filetree/file name=".prettierrc" >}}
  {{< filetree/file name="package-lock.json" >}}
  {{< filetree/file name="README.md" >}}
  {{< filetree/file name="svelte.config.js" >}}
  {{< filetree/file name="vite.config.js" >}}
{{< /filetree/container >}}

We're gonna write our code in the **+page.svelte** file in the routes folder

### Logic
Before we start writing our code, lets plan out what our app should generally look like.


[Resistor](/static/images/band.png)

We want to have buttons, a result area to see the resistance and a resistor image that changes based on the colour selected from the buttons.

### Code

{{% steps %}}

### Step 1
The first three bands have the same colours which correspond to the same numbers. Therefore we can reuse this object for each band.

As each colour corresponds/maps to 1 number a dictionary/hashmap/object is the perfect data structure to hold this data.

```javascript
const value_to_colour = {
		0: '#141412',
		1: '#744418',
		2: '#A71717',
		3: '#D4770D',
		4: '#D6D600',
		5: '#206916',
		6: '#0E1A63',
		7: '#5B106E',
		8: '#797979',
		9: '#FAFAFA'
	};
```
Band 4 on the other hand will be slightly different so we can create its own Object
```javascript
const band4_value_to_colour = {
		0: '#d9bb7a',
		1: '#744418',
		2: '#A71717',
		0.5: '#206916',
		0.25: '#0E1A63',
		0.1: '#5B106E',
		0.05: '#797979',
		5: '#FFD700',
		10: '#FAFAFA'
	};
```

### Step 2
Next we will create a main div to hold everything and a band-select div to hold our dropdown buttons for each band. For the dropdown button we will use a  ```<select>``` tag which has ```<option>``` tags as children

```html
<div>
	<label for="band1" class="label">Band 1</label>
	<select
		id="select-band1"
		name="band1"
		class="select"
	>
		<option value="0" style="background-color: #141412; color: white;">Black</option>
		<option value="1" style="background-color: #744418; color: white;">Brown</option>
		<option value="2" style="background-color: #A71717; color: white;">Red</option>
		<option value="3" style="background-color: #D4770D; color: white;">Orange</option>
		<option value="4" style="background-color: #D6D600; color: white;">Yellow</option>
		<option value="5" style="background-color: #206916; color: white;">Green</option>
		<option value="6" style="background-color: #0E1A63; color: white;">Blue</option>
		<option value="7" style="background-color: #5B106E; color: white;">Violet</option>
		<option value="8" style="background-color: #797979; color: white;">Grey</option>
		<option value="9" style="background-color: #FAFAFA; color: black;">White</option>
	</select>
</div>
```

### Step 3


{{% /steps %}}

### Conclusion
