# Frontend Mentor - Equalizer landing page solution

This is a solution to the [Equalizer landing page challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/equalizer-landing-page-7VJ4gp3DE). Frontend Mentor challenges help you improve your coding skills by building realistic projects. 

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
- [Author](#author)

## Overview

### The challenge

Users should be able to:

- View the optimal layout depending on their device's screen size
- See hover states for interactive elements

### Links

- Solution URL: [Add solution URL here](https://your-solution-url.com)
- [Live site](https://mainlycolors.github.io/equalizer-landing-page/)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- CSS Grid
- Mobile-first workflow

### What I learned

The middle section of the site was a tricky overlap of multiple elements but I approached the problem with a somewhat complex CSS grid explained below

# HTML
To start the HTML looks like this: 

```html
    <main>
      <img
        class="phone-img"
        src="./design/assets/illustration-app.png"
        alt="image of app concept"
      />
      <div class="black-bg">
        <img src="./design/assets/bg-pattern-2.svg" alt="" />
      </div>
      <div class="premium-card">
        <h2>Premium EQ</h2>
        <p>
          Get expert-level control with a robust equalizer, volume mixer, and
          spatial audio. Take your listening experience to a whole new level and
          access all our incredible features!
        </p>
        <div class="per-month-container">
          <span>&dollar;4</span>
          <span>/ month</span>
        </div>
        <a href="#" class="download-btn ios-btn">
          <span
            ><img
              src="./design/assets/icon-apple.svg"
              alt="Apple Inc Logo"
              srcset=""
            />
          </span>
          iOS Download
        </a>
        <a href="#" class="download-btn android-btn">
          <span
            ><img
              src="./design/assets/icon-android.svg"
              alt="Android Inc Logo"
              srcset=""
            />
          </span>
          Android Download</a
        >
      </div>
    </main>
```

# CSS - Mobile Design 📱

For the mobile design there only needs to be 1 column with 5 rows and then each section can be assigned accordly 
```css
 main {
    margin-bottom: clamp(4rem, 11.59vw, 5.5625rem);
    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows:
      6.125rem /*top of phone img*/
      20.75rem /*between black bg & top premium card */
      3rem /*between top premium card & bottom phone img */
      13.75rem /*between bottom phone img & bottom black bg */
      20.375rem; /*between bottom black bg & bottom premium card */
  }
  
.phone-img {
  display: block;
  margin: 0 auto;
  width: clamp(13.0625rem, 35.156vw, 19.5rem);
  height: auto;
  grid-column: 1 / 2;
  grid-row: 1 / 3;
  z-index: 1;
}

.black-bg {
  width: 100%;
  height: 37.5rem;
  background-color: var(--clr-font-primary);
  border-radius: 0.75rem;
  grid-column: 1 / 2;
  grid-row: 2 / 5;
}

.black-bg img {
  --change-rate: 12.8vw;
  display: block;
  margin-left: clamp(3rem, var(--change-rate), 21rem);
  width: clamp(17.5rem, 36.46vw, 19.5rem);
  height: auto;
}

.premium-card {
  padding-left: clamp(2.25rem, 6.25vw, 3.375rem);
  padding-top: clamp(3rem, 6.25vw, 3.625rem);
  width: clamp(23.4375rem, 51.95vw, 27.875rem);
  height: clamp(34.125rem, 71.1vw, 39.0625rem);
  background-color: var(--clr-bg-primary);
  border-radius: 0.75rem;
  grid-column: 1 / 2;
  grid-row: 4 / 6;
  z-index: 2;
}

```
# CSS - Tablet Design

The tablet view gets a little more complicated, now we need 5 rows and 5 columns for each section. The grid is broken up into each section where a object starts or stops. I tried to make these values responsive for the desktop view but there was no easy way since the design breaks out of its tablet groupings.

```css
@media screen and (min-width: 37.5rem) {
  main {
    width: clamp(43.5rem, 90.625vw, 69.375rem);
    margin-left: auto;
    margin-right: auto;

    /* 43.5rem total */
    grid-template-columns:
      9.19% /*left black-bg - 4rem*/
      25.14% /*left phone img to left premium card - 10.9375rem*/
      13.65% /*left premium card to right phone img - 5.9375rem*/
      43.678% /*right phone img to right premium card - 19rem*/
      08.33% /*right black-bg 3.625rem*/;

    grid-template-rows:
      8.625rem /*top of phone img*/
      9.375rem /*between black bg & top premium card */
      16.75rem /*between top premium card & bottom phone img */
      11.375rem /*between bottom phone img & bottom black bg */
      6rem; /*between bottom black bg & bottom premium card */
  }

  .phone-img {
    grid-column: 2 / 4;
    grid-row: 1 / 4;
  }

  .black-bg {
    grid-column: 1 / 6;
  }

  .black-bg img {
    --change-rate: 29.8vw;
    --negative-top-margin: clamp(1.9375rem, 4.036vw, 2.5rem);
    margin-top: calc(var(--negative-top-margin) * -1);
  }

  .premium-card {
    grid-column: 3 / 5;
    grid-row: 3 / 6;
  }
  }
```
# CSS - Desktop Design 🖥

The Desktop view is similar to the tablet with some values changed

```css
@media screen and (min-width: 69.375rem) {
  main {
    /* 69.375rem total */
    grid-template-columns:
      9.19% /*left black-bg - 102px 6.375rem*/
      28.11% /*left phone img to left premium card - 312px 19.5rem*/
      13.96% /*left premium card to right phone img - 155px 9.6875rem*/
      40.18% /*right phone img to right premium card - 446px 27.875rem*/
      08.56% /*right black-bg 95px 5.9375rem*/;
    grid-template-rows:
      13.3125rem /*top of phone img*/
      5.625rem /*between black bg & top premium card */
      21.1875rem /*between top premium card & bottom phone img */
      10.6875rem /*between bottom phone img & bottom black bg */
      7.1875rem; /*between bottom black bg & bottom premium card */
  }

  .phone-img {
    grid-column: 2 / 3;
  }

  .premium-card {
    grid-column: 4 / 5;
  }
}
```

## Author

- Frontend Mentor - [@MainlyColors](https://www.frontendmentor.io/profile/MainlyColors)
- Twitter - [@MainlyColors](https://www.twitter.com/MainlyColors)

