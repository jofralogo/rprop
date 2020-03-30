# rProp: Responsive SCSS mixins
**rProp** is a super-easy way to define any CSS property and their values for phone, tablet and desktop.
- - -

## How to
1. Import it in your sass/scss file: `@import 'rprop';`
2. Include it whenever you need: 
```scss
@include rprop(
  $prop,
  $small-value, 
  $medium-value, 
  $large-value);
```

## Mixin atributes and media-queries
- `$prop` = CSS Property 
- `$small-value` = Value **from** 0px screen width.
- `$medium-value` = Value for **at least** 641px screen width.
- `$large-value` = Value for **at least** 1025px screen width.

Note: Breakpoints values can be edited in *rprop.scss* file.

## Example

This code:
```scss
h1{
  @include rprop(font-size, 1rem, 1.5rem, 1.8rem);
}
```

Will be transformed into:
```css
  h1 {
    font-size: 1rem;
  }

@media only screen and (min-width: 641px) { 
  h1 { 
    font-size: 1.5rem; 
  } 
}

@media only screen and (min-width: 1025px) { 
  h1 { 
    font-size: 1.8rem; 
  } 
}
```

## Specify a value for a specific *Media-Query*
Do you want to define a property for a specific screen size only?
No problem, you can use one of these mixins:
```scss
@include smallprop($prop,$value);
```
```scss
@include mediumprop($prop,$value);
```
```scss
@include largeprop($prop,$value);
```
```scss
@include xlargeprop($prop,$value);
```
```scss
@include xxlargeprop($prop,$value);
```

## Extended control
I've been using `rProp` mixin for a while and it cover most cases that I needed but I created another mixin called `rpropX` for a more extended control and play with longest screen size ranges.

- `$xlarge-value` = Value for **at least** 1441px screen width.
- `$xxlarge-value`  = Value for **at least** 1921px screen width.

**NOTE:** If you don't want to set a value for a specific Media-Query screen range you can set it to `null`, `_` or `n` (don't leave it empty). In that case, that screen range will inherit the property of its closest smaller breakpoint.

## Example for extended control
```scss
h2{
  @include rpropX(font-size, 24px, 32px, 44px, 56px, 64px);
}
```

Will be transformed into:
```css
h2 { 
  font-size: 24px; 
}

@media only screen and (min-width: 641px){ 
  h1 { 
    font-size: 32px; 
  } 
}

@media only screen and (min-width: 1025px) { 
  h1 { 
    font-size: 44px; 
  } 
}  

@media only screen and (min-width: 1441px) { 
  h1 { 
    font-size: 56px; 
  } 
}

@media only screen and (min-width: 1921px) { 
  h1 { 
    font-size: 64px; 
  } 
}
```
