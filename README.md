# rProp
**Responsive SCSS mixins**
A super-easy way to define any CSS property and their values for phone, tablet and desktop.
- - -

## How to
1. Import it in your sass/scss file: `@import 'rprop';`
2. Include it:
```scss
@include rprop(
	$prop,
	$small-value, 
	$medium-value, 
	$large-value);
```

## Mixin atributes
- $prop = CSS Property 
- $small-value = Value from 0px.
- $medium-value = Value for at least 641px (40.063em).
- $large-value  = Value for at least 1025px (64.063em).

## Example

This code:
```scss
h1{
  @include rprop(font-size, 22, 32, 42);
}
```

Will compile:
```sass
h1 {font-size: 22;}
@media only screen and (min-width: 641px) { h1 { font-size: 32; } }
@media only screen and (min-width: 1025px) { h1 { font-size: 42; } }
```

## Specify a value for an specific Media-Query
Do you want to define a property for a specific screen size only? No problem
You can use one of these mixins:
```scss
smallprop($prop,$value);
mediumprop($prop,$value);
largeprop($prop,$value);
xlargeprop($prop,$value);
xxlargeprop($prop,$value);
`

## Extended control
I've been using 'rProp' mixin for a while and it cover most cases that I needed but I created another mixin called 'rpropX' for an extended control and play with longest screen size ranges.

- $xlarge-value = Value for at least 1441px.
- $xxlarge-value = Value for at least 1921px.

**NOTE:** If you don't want to set a value for a specific Media-Query screen range you can set it to "null", "_" or "n" (it must have a value, don't leave it empty). In that case, that screen range will inherit the property of its closest smaller range.

## Example for extended control
```scss
h2{
  @include rpropX(font-size, 22, 32, 42, 52, 62);
}
```

Will compile:
```scss
h1 { font-size: 22; }
@media only screen and (min-width: 641px) { h1 { font-size: 32; } }
@media only screen and (min-width: 1025px) { h1 { font-size: 42; } }  
@media only screen and (min-width: 1441px) { h1 { font-size: 52; } }
@media only screen and (min-width: 1921px) { h1 { font-size: 62; } }
```