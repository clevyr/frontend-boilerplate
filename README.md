# SCSS

----

### Linter 
- Uses stylelint
- Configuration in `.stylelintrc.json`

---
### Variables  
`$grid-breakpoints` - custom breakpoint values from Bootstrap  
##### Fonts  
- `$base-font-size` - 16px, the font size for the `body` tag;
- `$title-font` - Font family for titles
- `$body-font` - Font family for body copy, set on `body` element  
##### CSS Transition Easings  
- `$timing` -  global transition timing;
- `$ease: cubic-bezier(0.4, 0.25, 0.3, 1); ` - custom ease function
- `$ease-out: cubic-bezier(0.25, 0.46, 0.45, 0.94);` - custom ease out function

---

### Containers  
The `.container` class is overwrite in `core/_container.scss`. The changes overwrite the bootstrap container for a more fluid layout.

---

### Mixins
#### Font Sizes
- `rem(font size in pixels)` - creates a `rem` font size from the value of the px font size
- `em(font size in pixels)` - creates a relative font size (`em`) from the value of the px font size

#### Browser Hacks
Located in `mixins/_browsers.scss`. You can use these mixins to target specific browsers. You can find more information or configurations at http://browserhacks.com/
Example:
```
@include ie-only() { 
    // IE only styles here 
}
```

#### Fluid Type
To include a "fluid type" font size, utilize the `@fluid-type` mixin.   
Example: 
```
h1 {
    @include fluid-type(map_get($grid-breakpoints, sm), 1500px, 25px, 65px);
}
```  
This will set the font size to: 
 - 65px for screens larger than 1500px.
 - 25px for screens smaller than the small grid breakpoint variable
 - Between those two screen sizes, the font size will automatically adjust so the content fits in the same area (no line breaks)
 
#### Media Queries
*Note: The $size variable is optional, the default is the small breakpoint*  
- `@include mq-max($size) {}` - creates a max-size media query  
- `@include mq-min($size) {}` - creates a min-size media query  
- `@include mq-max-min($maxSize, $minSize) {}` - creates a media query between the minimum and maximum sizes
- `@include mq-max-height($size) {}` - creates a max-height media query
- `@include mq-min-height($size) {}` - creates a min-height media query

#### Input Placeholder
Styles the placeholder for form inputs, includes vendor prefixing
```
@include placeholder {
    // placeholder styles...
}
```

#### Positioning
Centers objects via positioning and transform attributes 
- `@include center()`
- `@include center-horizontally()`
- `@include center-vertically()`
- `@include clearfix()`

#### Visibility
`@include hidden()` - visibly hides element while keeping the initial display value in place. This can be useful when needing to hide an element until a JS function is initialized.
