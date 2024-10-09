## file structure

style/test
├── 1.Layout  
│ ├── AspectRatio.scss  
│ ├── BoxDecorationBreak.scss  
│ ├── BoxSizing.scss  
│ ├── usage.md  
│ └── ...  
├── 2.FlexboxGrid
└── ...

[Same as Tailwind web](https://tailwindcss.com/docs/aspect-ratio)

### style file - generate SCSS file

- For categorizing mixins within @if, I need the mixin to be commented out.

### test file - testing SCSS before use

- Run all 79067 test cases.

```bash
bun install
bun test
```

## How to generate SCSS file?

### 1. Use 'Live Sass Compiler'(Extension) to compile index.css (src/style/index.css)

### 2. Use SEARCH feature(VSCode) to remove below in index.css

```
/*x and x*/
```

### 3. Rename your index.css

### 4. Ready to serve!
