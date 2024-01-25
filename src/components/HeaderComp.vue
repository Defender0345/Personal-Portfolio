<script setup>
import HomeAComp from './HomeAComp.vue'
import HomeCComp from './HomeCComp.vue'

class TypeWriter {
  constructor(txtElement, words, wait = 2500) {
    this.txtElement = txtElement
    this.words = words
    this.txt = ''
    this.wordIndex = 0
    this.wait = parseInt(wait, 10)
    this.type()
    this.isDeleting = false
  }

  type() {
    // Current index of word
    const current = this.wordIndex % this.words.length
    // Get full text of current word
    const fullTxt = this.words[current]

    // Check if deleting
    if (this.isDeleting) {
      // Remove char
      this.txt = fullTxt.substring(0, this.txt.length - 1)
    } else {
      // Add char
      this.txt = fullTxt.substring(0, this.txt.length + 1)
    }

    // Insert txt into element
    this.txtElement.innerHTML = `<span class="txt">${this.txt}</span>`

    // Initial Type Speed
    let typeSpeed = 200

    if (this.isDeleting) {
      typeSpeed /= 2
    }

    // If word is complete
    if (!this.isDeleting && this.txt === fullTxt) {
      // Make pause at end
      typeSpeed = this.wait
      // Set delete to true
      this.isDeleting = true
    } else if (this.isDeleting && this.txt === '') {
      this.isDeleting = false
      // Move to next word
      this.wordIndex++
      // Pause before start typing
      typeSpeed = 500
    }

    setTimeout(() => this.type(), typeSpeed)
  }
}

// Init On DOM Load
document.addEventListener('DOMContentLoaded', init)

// Init App
function init() {
  const txtElement = document.querySelector('.txt-type')
  const words = JSON.parse(txtElement.getAttribute('data-words'))
  const wait = txtElement.getAttribute('data-wait')
  // Init TypeWriter
  new TypeWriter(txtElement, words, wait)
}
</script>

<template>
  <header id="header-home">
    <div class="container">
      <div class="header-content">
        <h1 class="py-4">
          I Am Dylan,
          <span class="txt-type" data-wait="2500" data-words='["A Web Developer"]'></span>
        </h1>
        <a href="work.html" class="btn-light">View My Work</a>
      </div>
    </div>
  </header>
  <HomeAComp />
  <HomeCComp />
  <RouterView />
</template>

<style lang="scss">
@import '@/assets/_shared.scss';
</style>
