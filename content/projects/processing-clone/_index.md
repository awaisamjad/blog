---
title : Processing Clone
date : 2024-02-05T18:06:37Z
draft : false
---
{{< callout type="warning" >}}
  This project is still in development
{{< /callout >}}

## Description
This project is a simple attempt to create a processing clone

If you havent tried processing check it out at [Processing](https://processing.org)

As per the website, **Processing is a flexible software sketchbook and a language for learning how to code** and was my first introduction to programming in 2021. I used it during university and learnt many fundamnetal concepts such as variables, loops, functions, classes etc. 

You can create many visual elements and shapes such as squares, lines, texts and basically do stuff with them

Below is a GIF of it in action

{{< callout type="error" >}}
  Insert GIF
{{< /callout >}}

## How it works
Processing itself isnt open source so we cant look at the code used to make it. But that doesnt mean we cant figure out how it basically works. 
#### The text editor
This is the main part of the processing apllication and where you write the code. At the top we can see some buttons, a run and stop button etc

{{< callout type="error" >}}
  Insert Image
{{< /callout >}}

#### The Output Window
This is the output of what we instructed our code to do. Its the visual stuff

{{< callout type="error" >}}
  Insert Image
{{< /callout >}}

#### Interpreter
Before our code can actually do something, it needs to be interpreted by another language to create a window with what we want. I dont know what language processing uses but for our clone we will be using Rust.

below is a list of the technologies/tools we will be using

#### Technologies/Tools
1. Tauri - A framework for building tiny, blazingly fast binaries for all major desktop platforms.
   - Frontend : Vanilla JavaScript
   - Backend : Rust
2. MiniFb - A cross platform library written in Rust that makes it easy to setup a window and to display a 32-bit pixel buffer. This will be used to make our graphics window
3. WC Monaco Editor - An easy embed of the Monaco Editor. The Monaco Editor was made by Microsoft and is used by VSCode 


## Prerequisites
We can now start getting our tools
{{% steps %}}

### Rust

This is the first step.

### Tauri

This is the second step.

### WC Monaco Editor


### 
{{% /steps %}}