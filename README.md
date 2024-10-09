![logo](https://github.com/ESCSS-labs/ESCSS/blob/main/assets/logo.png)

# What is ESCSS-SCSS?

ESCSS-SCSS takes the full potential of CSS and Tailwind in SCSS.

## Core Concept - Atomic CSS

Atomic CSS abstraction ensures optimal performance and consistent styling.

```scss
// An Atomic CSS mixin contains CSS properties with breakpoints, e.g.
@mixin margin($v, $rwd: null) {
  @if $rwd==null {
    margin: $v;
  } @else {
    @media (min-width: $rwd) {
      margin: $v;
    }
  }
}
```

## Requirements

version >= 1.23.0

## Usages

### Set your project's breakpoints.

```scss
// _awaken.scss
$_sm: 0px !default;
$_md: 0px !default;
$_lg: 0px !default;
$_xl: 0px !default;
$_xxl: 0px !default;
```

### Same utility names and behaviors as Tailwind

- Support: basic utilities、media query、dark mode

### Type @include utils/experiments to show more API

- Instal 'SCSS IntelliSense' extension in VSCode

### @include utils_reset-tw in every id/class(Best Practice)

- to reset some tailwind behavior(be lazy)

### Transform from Tailwind to Sass:

```
    tailwind       -->       scss
        /                     \/
        []                    ()
-----------------------------------------------------
    m-1/2                 @include m-1\/2
    m-[20px]              @include m-(20px)
```

## Examples

### Color opacity

```scss
#Demo {
  @include text-green-50(65%);
  @include text-green-50(0.65);

  @include utils_reset-tw;
}
```

### Priority: same behavior as CSS

```scss
#Demo {
  background: red;
  @include bg-green-50; // override red

  @include utils_reset-tw;
}
```

### Developer Experience: Dark/Media query utility

```scss
#Demo {
  @include bg-gradient-to-r;
  @include from-cyan-500;
  @include to-blue-500;

  @include sm {
    @include from-black-500;
    @include to-white-500;
  }

  @include \2xl {
    @include from-amber-500;
    @include to-green-500;
  }

  // This is different from Tailwind as it combines class and media strategies:
  //  - Class strategy: Add a '--dark' class to the html/body/top level, and toggle the class using JavaScript.
  //  - Media strategy: Automatically handled for you when using the dark utility. Only be triggered if the user has set their browser to dark mode.
  @include dark {
    color: black;
    background-color: white;
  }

  @include utils_reset-tw;
}
```

## Q&A

### Why are the default values of breakpoints(sm、md..) set to 0px?

1. Each project has unique breakpoints, and it's relatively easy to trigger [AGPL-3.0, §13](https://www.gnu.org/licenses/agpl-3.0.en.html) obligations to open source, therefore set 0 as default.
2. I think it's fair to earn money for my work.

### What is the benefit of using Atomic CSS?

1. Faster updates in Vite.
2. Quicker loading of 'SCSS IntelliSense' (VS Code Extension).
3. Easier maintenance and study for both author and users.

### Do you support backward compatibility?

Yes, it is designed in mind from Sass v1.23.0 to the latest version if. I adhere to Sass’s deprecation warnings to ensure smooth transitions.

### Are you a Tailwind killer?

No, it is designed to reduce developers' frustration and work with Tailwind pretty well.

## Installation

### 1. copy SCSS file

### 2. install sass in your project

```shell
npm add -D sass-embedded # or sass
```

### 3. using Vite to set up SCSS file

```js
//  vite.config.js
export default defineConfig({
  css: {
    preprocessorOptions: {
      scss: {
        // your path
        additionalData: `
        @use 'src/assets/_awaken.scss' as *;
        `,
      },
    },
  },
});
```
