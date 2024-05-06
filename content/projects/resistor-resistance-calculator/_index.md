---
title : Resistor Resistance Calculator
date : 2024-02-23T17:20:45Z
draft : false
math : true
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

As each colour corresponds/maps directly to 1 number a dictionary/hashmap/object is the perfect data structure to hold this data.

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
_Notice that we made the `color : black` for option 9 as the background is white_

Repeat the code for bands 2 and 3. For band 4 make sure to change the colours.
### Step 3
Now we need a image of a resistor. We are gonna change the colour of the bands through the dropdown options. Therefore the best image format would be an svg. Find any SVG online or make you own. The one i used can be downloaded from here : [Resistor SVG](https://openclipart.org/detail/276048/47k-ohm-resistor)

### Step 4
Paste the svg code or link it in your html.

### Step 5

Now let's focus on the logic of our app. Depending on the colors chosen, we need to calculate the resistance. Here's how it works:

- The first band represents the units.
- The second band represents the tens.
- The third band represents the power to which the value is raised.

##### Example
Let Band 1 is Red, Band 2 is Brown, and Band 3 is Violet, the values would be: Band 1 = 2, Band 2 = 10, and Band 3 = 7.

To calculate the resistance, we add Band 1 and Band 2 to get 12, and then multiply it by 
$\(10^7\)$.

Resistors arent perfect components so therefore have some error. We handle this by inlcuding a tolerance which is shown through the 4th band. Let our 4th band be green. Therefore it has a ± 0.5 % tolerance. When we work thios out our we get the following :
210000000 ohms ± 1050000 ohms
{{% /steps %}}

### Conclusion
