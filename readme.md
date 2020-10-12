# SCSS Helpers Collection

## Install

```
npm install @wide/styles-helpers --save
```

## Note

Please, note that more you add helper mixins, more your CSS compiled file will be heavy.  

So add helpers you really need.

## Usage

- [a11y](#a11y)
- [alignment](#alignment)
- [clearfix](#clearfix)
- [container](#container)
- [crop](#crop)
- [display](#display)
- [embed](#embed)
- [flexbox](#flexbox)
- [float](#float)
- [font](#font)
- [overflow](#overflow)
- [position](#position)
- [stretched-link](#stretched-link)
- [text](#text)
- [visibility](#visibility)

<br />
<br/>

## a11y

- [Mixins](#a11y-mixins)
  - [`a11y-aria()`](#a11y-aria)
  - [`a11y-sr()`](#a11y-sr)
  - [`a11y()`](#a11y-a11y)

<br />

### <a name="a11y-mixins"></a>Mixins

#### <a name="a11y-aria"></a>`a11y-aria()`

ARIA roles display visual cursor hints.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.a11y-aria;
```

##### Output
```css
[aria-busy=true] {
    cursor: progress;
}
[aria-controls] {
    cursor: pointer;
}
[aria-disabled] {
    cursor: default;
}
```

#### <a name="a11y-sr"></a>`a11y-sr()`

Screen readers.

```scss
@use '@wide/styles-helpers' as helpers;

{
    @include helpers.a11y-sr();
}
```

##### Output
```css
.a11y-sr-only {
    border: 0 !important;
    clip: rect(0 0 0 0) !important;
    height: 1px !important;
    margin: 0 !important;
    overflow: hidden !important;
    padding: 0 !important;
    position: absolute !important;
    white-space: nowrap !important;
    width: 1px !important;
}
.a11y-sr-focus:not(:focus) {
    border: 0 !important;
    clip: rect(0 0 0 0) !important;
    height: 1px !important;
    margin: 0 !important;
    overflow: hidden !important;
    padding: 0 !important;
    position: absolute !important;
    white-space: nowrap !important;
    width: 1px !important;
}
```

#### <a name="a11y-a11y"></a>`a11y()`

Combine both [`a11y-aria`](#a11y-aria) and [`a11y-sr`](#a11y-sr) helpers in one helper.

```scss
@use '@wide/styles-helpers' as helpers;

{
    @include helpers.a11y();
}
```

##### Output
```css
[aria-busy=true] {
    cursor: progress;
}
[aria-controls] {
    cursor: pointer;
}
[aria-disabled] {
    cursor: default;
}

.a11y-sr-only {
    border: 0 !important;
    clip: rect(0 0 0 0) !important;
    height: 1px !important;
    margin: 0 !important;
    overflow: hidden !important;
    padding: 0 !important;
    position: absolute !important;
    white-space: nowrap !important;
    width: 1px !important;
}
.a11y-sr-focus:not(:focus) {
    border: 0 !important;
    clip: rect(0 0 0 0) !important;
    height: 1px !important;
    margin: 0 !important;
    overflow: hidden !important;
    padding: 0 !important;
    position: absolute !important;
    white-space: nowrap !important;
    width: 1px !important;
}
```

<br />
<br />

## alignment

- [Variables](#alignment-variables)
  - [`$aligns`](#alignment-variables-aligns)
  - [`$aligns-important`](#alignment-variables-aligns-important)
- [Mixins](#alignment-mixins)
  - [`alignment-helper()`](#alignment-helper)
  - [`alignment-helper-with-bp()`](#alignment-helper-with-bp)
  - [`alignment()`](#alignment-alignment)

<br />

### <a name="alignment-variables"></a>Variables

All those variables could be customized depending on what you need in your `variables.scss` file.  
Here are the default values.

#### <a name="alignment-variables-aligns"></a>`$aligns`
Define all alignment values to support.

```scss
$aligns: (
    baseline,
    bottom,
    middle,
    top,
    text-top,
    text-bottom
) !default;
```

#### <a name="alignment-variables-aligns-important"></a>`$aligns-important`
Set the important property on each rules.

```scss
$aligns-important: true;
```

<br />

### <a name="alignment-mixins"></a>Mixins

#### <a name="alignment-helper"></a>`alignment-helper()`

Set all alignments classes from the [`$aligns`](#alignment-variables-aligns) variable.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.alignment-helper;
```

##### Output
```css
.align-baseline {
    vertical-align: baseline !important;
}

.align-bottom {
    vertical-align: bottom !important;
}

.align-middle {
    vertical-align: middle !important;
}

.align-top {
    vertical-align: top !important;
}

.align-text-top {
    vertical-align: text-top !important;
}

.align-text-bottom {
    vertical-align: text-bottom !important;
}

.align-vcenter {
    font-size: 0;
}
.align-vcenter::before {
    content: "";
    display: inline-block;
    height: 100%;
    vertical-align: middle;
}
.align-vcenter > * {
    display: inline-block;
    font-size: 1rem;
    vertical-align: middle;
}
```

#### <a name="alignment-helper-with-bp"></a>`alignment-helper-with-bp()`

Set all alignments classes from the [`$aligns`](#alignment-variables-aligns) variable with breakpoints media queries.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.alignment-helper-with-bp;
```

##### Output
```css
@media (min-width: 20.375em) and (max-width: 35.99875em) {
    .align-baseline\@xs-only {
        vertical-align: baseline !important;
    }

    .align-bottom\@xs-only {
        vertical-align: bottom !important;
    }

    .align-middle\@xs-only {
        vertical-align: middle !important;
    }

    .align-top\@xs-only {
        vertical-align: top !important;
    }

    .align-text-top\@xs-only {
        vertical-align: text-top !important;
    }

    .align-text-bottom\@xs-only {
        vertical-align: text-bottom !important;
    }

    .align-vcenter\@xs-only {
        font-size: 0;
    }
    .align-vcenter\@xs-only::before {
        content: "";
        display: inline-block;
        height: 100%;
        vertical-align: middle;
    }
    .align-vcenter\@xs-only > * {
        display: inline-block;
        font-size: 1rem;
        vertical-align: middle;
    }
}
@media (min-width: 36em) {
 /*
  * .align-baseline\@sm
  * .align-bottom\@sm
  * .align-middle\@sm
  * .align-top\@sm
  * .align-text-top\@sm
  * .align-text-bottom\@sm
  * .align-vcenter\@sm
  * .align-vcenter\@sm::before
  * .align-vcenter\@sm > *
  */
}
@media (min-width: 36em) and (max-width: 47.99875em) {
 /*
  * .align-baseline\@sm-only
  * .align-bottom\@sm-only
  * .align-middle\@sm-only
  * .align-top\@sm-only
  * .align-text-top\@sm-only
  * .align-text-bottom\@sm-only
  * .align-vcenter\@sm-only
  * .align-vcenter\@sm-only::before
  * .align-vcenter\@sm-only > *
  */
}
@media (min-width: 48em) {
 /*
  * .align-baseline\@md
  * .align-bottom\@md
  * .align-middle\@md
  * .align-top\@md
  * .align-text-top\@md
  * .align-text-bottom\@md
  * .align-vcenter\@md
  * .align-vcenter\@md::before
  * .align-vcenter\@md > *
  */
}
@media (min-width: 48em) and (max-width: 63.99875em) {
 /*
  * .align-baseline\@md-only
  * .align-bottom\@md-only
  * .align-middle\@md-only
  * .align-top\@md-only
  * .align-text-top\@md-only
  * .align-text-bottom\@md-only
  * .align-vcenter\@md-only
  * .align-vcenter\@md-only::before
  * .align-vcenter\@md-only > *
  */
}
@media (min-width: 64em) {
 /*
  * .align-baseline\@lg
  * .align-bottom\@lg
  * .align-middle\@lg
  * .align-top\@lg
  * .align-text-top\@lg
  * .align-text-bottom\@lg
  * .align-vcenter\@lg
  * .align-vcenter\@lg::before
  * .align-vcenter\@lg > *
  */
}
@media (min-width: 64em) and (max-width: 74.99875em) {
 /*
  * .align-baseline\@lg-only
  * .align-bottom\@lg-only
  * .align-middle\@lg-only
  * .align-top\@lg-only
  * .align-text-top\@lg-only
  * .align-text-bottom\@lg-only
  * .align-vcenter\@lg-only
  * .align-vcenter\@lg-only::before
  * .align-vcenter\@lg-only > *
  */
}
@media (min-width: 75em) {
 /*
  * .align-baseline\@xl
  * .align-bottom\@xl
  * .align-middle\@xl
  * .align-top\@xl
  * .align-text-top\@xl
  * .align-text-bottom\@xl
  * .align-vcenter\@xl
  * .align-vcenter\@xl::before
  * .align-vcenter\@xl > *
  */
}
@media (min-width: 75em) and (max-width: 99.99875em) {
 /*
  * .align-baseline\@xl-only
  * .align-bottom\@xl-only
  * .align-middle\@xl-only
  * .align-top\@xl-only
  * .align-text-top\@xl-only
  * .align-text-bottom\@xl-only
  * .align-vcenter\@xl-only
  * .align-vcenter\@xl-only::before
  * .align-vcenter\@xl-only > *
  */
}
@media (min-width: 100em) {
 /*
  * .align-baseline\@xxl
  * .align-bottom\@xxl
  * .align-middle\@xxl
  * .align-top\@xxl
  * .align-text-top\@xxl
  * .align-text-bottom\@xxl
  * .align-vcenter\@xxl
  * .align-vcenter\@xxl::before
  * .align-vcenter\@xxl > *
  */
}
@media (min-width: 100em) {
 /*
  * .align-baseline\@xxl-only
  * .align-bottom\@xxl-only
  * .align-middle\@xxl-only
  * .align-top\@xxl-only
  * .align-text-top\@xxl-only
  * .align-text-bottom\@xxl-only
  * .align-vcenter\@xxl-only
  * .align-vcenter\@xxl-only::before
  * .align-vcenter\@xxl-only > *
  */
}
```

#### <a name="alignment-alignment"></a>`alignment()`

Helper `alignment` entry point  
Combine both [`alignment-helper`](#alignment-helper) and [`alignment-helper-with-bp`](#alignment-helper-with-bp) helpers in one helper.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.alignment;
// @include helpers.alignment(false);
```

###### Parameters
| Type | Description | Mandatory | Default |
|---|---|---|---|
| `Boolean` | Use `alignment-helper-with-bp()` | `false` | `true` |

##### Output
See [`alignment-helper`](#alignment-helper) and [`alignment-helper-with-bp`](#alignment-helper-with-bp) outputs.

<br />
<br />

## clearfix

- [Mixins](#clearfix-mixins)
  - [`clearfix()`](#clearfix-clearfix)

<br />

### <a name="clearfix-mixins"></a>Mixins

#### <a name="clearfix-clearfix"></a>`clearfix()`

Define a `.clearfix` class.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.clearfix;
```

##### Output
```css
.clearfix::after {
    clear: both;
    content: "";
    display: block;
}
```

<br />
<br />

## crop

- [Mixins](#crop-mixins)
  - [`crop-helper()`](#crop-helper)
  - [`crop-helper-with-bp()`](#crop-helper-with-bp)
  - [`crop()`](#crop-crop)

<br />

### <a name="crop-mixins"></a>Mixins

#### <a name="crop-helper"></a>`crop-helper()`

Provide a cropping container in order to display media (usually images) cropped to certain ratios.  

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.crop-helper;
```

##### Output
```css
.crop {
    display: block;
    position: relative;
    overflow: hidden;
}
.crop.-r1\:1 {
    padding-bottom: 100%;
}
.crop.-r2\:1 {
    padding-bottom: 50%;
}
.crop.-r3\:2 {
    padding-bottom: 66.6666666667%;
}
.crop.-r4\:3 {
    padding-bottom: 75%;
}
.crop.-r5\:3 {
    padding-bottom: 60%;
}
.crop.-r5\:4 {
    padding-bottom: 80%;
}
.crop.-r6\:5 {
    padding-bottom: 83.3333333333%;
}
.crop.-r7\:3 {
    padding-bottom: 42.8571428571%;
}
.crop.-r11\:8 {
    padding-bottom: 72.7272727273%;
}
.crop.-r16\:9 {
    padding-bottom: 56.25%;
}
.crop.-r16\:10 {
    padding-bottom: 62.5%;
}
.crop_content,
.crop > iframe,
.crop > embed,
.crop > object,
.crop > video,
.crop > picture,
.crop > img {
    position: absolute;
    top: 0;
    left: 0;
    max-width: none;
}
.crop_content.-right,
.crop > iframe.-right,
.crop > embed.-right,
.crop > object.-right,
.crop > video.-right,
.crop > picture.-right,
.crop > img.-right {
    right: 0;
    left: auto;
}
.crop_content.-bottom,
.crop > iframe.-bottom,
.crop > embed.-bottom,
.crop > object.-bottom,
.crop > video.-bottom,
.crop > picture.-bottom,
.crop > img.-bottom {
    top: auto;
    bottom: 0;
}
.crop_content.-center,
.crop > iframe.-center,
.crop > embed.-center,
.crop > object.-center,
.crop > video.-center,
.crop > picture.-center,
.crop > img.-center {
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
```

#### <a name="crop-helper-with-bp"></a>`crop-helper-with-bp()`

Provide a cropping container in order to display media (usually images) cropped to certain ratios with breakpoints media queries.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.crop-helper-with-bp;
```

##### Output
```css
@media (min-width: 20.375em) and (max-width: 35.99875em) {
    .crop.-r1\:1\@xs-only {
        padding-bottom: 100%;
    }
    .crop.-r2\:1\@xs-only {
        padding-bottom: 50%;
    }
    .crop.-r3\:2\@xs-only {
        padding-bottom: 66.6666666667%;
    }
    .crop.-r4\:3\@xs-only {
        padding-bottom: 75%;
    }
    .crop.-r5\:3\@xs-only {
        padding-bottom: 60%;
    }
    .crop.-r5\:4\@xs-only {
        padding-bottom: 80%;
    }
    .crop.-r6\:5\@xs-only {
        padding-bottom: 83.3333333333%;
    }
    .crop.-r7\:3\@xs-only {
        padding-bottom: 42.8571428571%;
    }
    .crop.-r11\:8\@xs-only {
        padding-bottom: 72.7272727273%;
    }
    .crop.-r16\:9\@xs-only {
        padding-bottom: 56.25%;
    }
    .crop.-r16\:10\@xs-only {
        padding-bottom: 62.5%;
    }
}
@media (min-width: 36em) {
 /*
  * .crop.-r1\:1\@sm
  * .crop.-r2\:1\@sm
  * .crop.-r3\:2\@sm
  * .crop.-r4\:3\@sm
  * .crop.-r5\:3\@sm
  * .crop.-r5\:4\@sm
  * .crop.-r6\:5\@sm
  * .crop.-r7\:3\@sm
  * .crop.-r11\:8\@sm
  * .crop.-r16\:9\@sm
  * .crop.-r16\:10\@sm
  */
}
@media (min-width: 36em) and (max-width: 47.99875em) {
 /*
  * .crop.-r1\:1\@sm-only
  * .crop.-r2\:1\@sm-only
  * .crop.-r3\:2\@sm-only
  * .crop.-r4\:3\@sm-only
  * .crop.-r5\:3\@sm-only
  * .crop.-r5\:4\@sm-only
  * .crop.-r6\:5\@sm-only
  * .crop.-r7\:3\@sm-only
  * .crop.-r11\:8\@sm-only
  * .crop.-r16\:9\@sm-only
  * .crop.-r16\:10\@sm-only
  */
}
@media (min-width: 48em) {
 /*
  * .crop.-r1\:1\@md
  * .crop.-r2\:1\@md
  * .crop.-r3\:2\@md
  * .crop.-r4\:3\@md
  * .crop.-r5\:3\@md
  * .crop.-r5\:4\@md
  * .crop.-r6\:5\@md
  * .crop.-r7\:3\@md
  * .crop.-r11\:8\@md
  * .crop.-r16\:9\@md
  * .crop.-r16\:10\@md
  */
}
@media (min-width: 48em) and (max-width: 63.99875em) {
 /*
  * .crop.-r1\:1\@md-only
  * .crop.-r2\:1\@md-only
  * .crop.-r3\:2\@md-only
  * .crop.-r4\:3\@md-only
  * .crop.-r5\:3\@md-only
  * .crop.-r5\:4\@md-only
  * .crop.-r6\:5\@md-only
  * .crop.-r7\:3\@md-only
  * .crop.-r11\:8\@md-only
  * .crop.-r16\:9\@md-only
  * .crop.-r16\:10\@md-only
  */
}
@media (min-width: 64em) {
 /*
  * .crop.-r1\:1\@lg
  * .crop.-r2\:1\@lg
  * .crop.-r3\:2\@lg
  * .crop.-r4\:3\@lg
  * .crop.-r5\:3\@lg
  * .crop.-r5\:4\@lg
  * .crop.-r6\:5\@lg
  * .crop.-r7\:3\@lg
  * .crop.-r11\:8\@lg
  * .crop.-r16\:9\@lg
  * .crop.-r16\:10\@lg
  */
}
@media (min-width: 64em) and (max-width: 74.99875em) {
 /*
  * .crop.-r1\:1\@lg-only
  * .crop.-r2\:1\@lg-only
  * .crop.-r3\:2\@lg-only
  * .crop.-r4\:3\@lg-only
  * .crop.-r5\:3\@lg-only
  * .crop.-r5\:4\@lg-only
  * .crop.-r6\:5\@lg-only
  * .crop.-r7\:3\@lg-only
  * .crop.-r11\:8\@lg-only
  * .crop.-r16\:9\@lg-only
  * .crop.-r16\:10\@lg-only
  */
}
@media (min-width: 75em) {
 /*
  * .crop.-r1\:1\@xl
  * .crop.-r2\:1\@xl
  * .crop.-r3\:2\@xl
  * .crop.-r4\:3\@xl
  * .crop.-r5\:3\@xl
  * .crop.-r5\:4\@xl
  * .crop.-r6\:5\@xl
  * .crop.-r7\:3\@xl
  * .crop.-r11\:8\@xl
  * .crop.-r16\:9\@xl
  * .crop.-r16\:10\@xl
  */
}
@media (min-width: 75em) and (max-width: 99.99875em) {
 /*
  * .crop.-r1\:1\@xl-only
  * .crop.-r2\:1\@xl-only
  * .crop.-r3\:2\@xl-only
  * .crop.-r4\:3\@xl-only
  * .crop.-r5\:3\@xl-only
  * .crop.-r5\:4\@xl-only
  * .crop.-r6\:5\@xl-only
  * .crop.-r7\:3\@xl-only
  * .crop.-r11\:8\@xl-only
  * .crop.-r16\:9\@xl-only
  * .crop.-r16\:10\@xl-only
  */
}
@media (min-width: 100em) {
 /*
  * .crop.-r1\:1\@xxl
  * .crop.-r2\:1\@xxl
  * .crop.-r3\:2\@xxl
  * .crop.-r4\:3\@xxl
  * .crop.-r5\:3\@xxl
  * .crop.-r5\:4\@xxl
  * .crop.-r6\:5\@xxl
  * .crop.-r7\:3\@xxl
  * .crop.-r11\:8\@xxl
  * .crop.-r16\:9\@xxl
  * .crop.-r16\:10\@xxl
  */
}
@media (min-width: 100em) {
 /*
  * .crop.-r1\:1\@xxl-only
  * .crop.-r2\:1\@xxl-only
  * .crop.-r3\:2\@xxl-only
  * .crop.-r4\:3\@xxl-only
  * .crop.-r5\:3\@xxl-only
  * .crop.-r5\:4\@xxl-only
  * .crop.-r6\:5\@xxl-only
  * .crop.-r7\:3\@xxl-only
  * .crop.-r11\:8\@xxl-only
  * .crop.-r16\:9\@xxl-only
  * .crop.-r16\:10\@xxl-only
  */
}
```

#### <a name="crop-crop"></a>`crop()`

Helper `crop` entry point.  
Combine both [`crop-helper`](#crop-helper) and [`crop-helper-with-bp`](#crop-helper-with-bp) helpers in one helper.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.crop;
// @include helpers.crop(false);
```

##### Parameters
| Type | Description | Mandatory | Default |
|---|---|---|---|
| `Boolean` | Use `crop-helper-with-bp()` | `false` | `true` |

##### Output
See [`crop-helper`](#crop-helper) and [`crop-helper-with-bp`](#crop-helper-with-bp) outputs.

<br />
<br />

## display

- [Variables](#display-variables)
  - [`$displays`](#display-variables-displays)
  - [`$displays-important`](#display-variables-displays-important)
  - [`$displays-prefix`](#display-variables-displays-prefix)
- [Mixins](#display-mixins)
  - [`display-helper()`](#display-helper)
  - [`display-helper-with-bp()`](#display-helper-with-bp)
  - [`display-print-helper()`](#display-print-helper)
  - [`display-screen-helper()`](#display-screen-helper)
  - [`display()`](#display-display)

<br />

### <a name="display-variables"></a>Variables

All those variables could be customized depending on what you need in your `variables.scss` file.  
Here are the default values.

#### <a name="display-variables-displays"></a>`$displays`
Define all display values to support.

```scss
$displays: (
    block,
    flex,
    inline,
    inline-block,
    inline-flex,
    list-item,
    none,
    table,
    table-cell,
    table-row
) !default;
```

#### <a name="display-variables-displays-important"></a>`$displays-important`
Set the important property on each rules.

```scss
$displays-important: true;
```

#### <a name="display-variables-displays-prefix"></a>`$displays-prefix`
Define the prefix of all display classes.

```scss
$displays-prefix: 'd-';
```

<br />

### <a name="display-mixins"></a>Mixins

#### <a name="display-helper"></a>`display-helper()`

Set all display classes from the [`$displays`](#display-variables-displays) variable.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.display-helper;
```

##### Output
```css
.d-block {
    display: block !important;
}

.d-flex {
    display: flex !important;
}

.d-inline {
    display: inline !important;
}

.d-inline-block {
    display: inline-block !important;
}

.d-inline-flex {
    display: inline-flex !important;
}

.d-list-item {
  display: list-item !important;
}

.d-none {
    display: none !important;
}

.d-table {
    display: table !important;
}

.d-table-cell {
    display: table-cell !important;
}

.d-table-row {
    display: table-row !important;
}
```

#### <a name="display-helper-with-bp"></a>`display-helper-with-bp()`

Set all display classes from the [`$displays`](#display-variables-displays) variable with breakpoints media queries.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.display-helper-with-bp;
```

##### Output
```css
@media (min-width: 20.375em) and (max-width: 35.99875em) {
    .d-block\@xs-only {
        display: block !important;
    }

    .d-flex\@xs-only {
        display: flex !important;
    }

    .d-inline\@xs-only {
        display: inline !important;
    }

    .d-inline-block\@xs-only {
        display: inline-block !important;
    }

    .d-inline-flex\@xs-only {
        display: inline-flex !important;
    }

    .d-list-item\@xs-only {
        display: list-item !important;
    }

    .d-none\@xs-only {
        display: none !important;
    }

    .d-table\@xs-only {
        display: table !important;
    }

    .d-table-cell\@xs-only {
        display: table-cell !important;
    }

    .d-table-row\@xs-only {
        display: table-row !important;
    }
}
/* and so on */
@media (min-width: 36em) {
    /*
     * .d-block\@sm
     * .d-flex\@sm
     * .d-inline\@sm
     * .d-inline-block\@sm
     * .d-inline-flex\@sm
     * .d-list-item\@sm
     * .d-none\@sm
     * .d-table\@sm
     * .d-table-cell\@sm
     * .d-table-row\@sm
     */
}
@media (min-width: 36em) and (max-width: 47.99875em) {
    /*
     * .d-block\@sm-only
     * .d-flex\@sm-only
     * .d-inline\@sm-only
     * .d-inline-block\@sm-only
     * .d-inline-flex\@sm-only
     * .d-list-item\@sm-only
     * .d-none\@sm-only
     * .d-table\@sm-only
     * .d-table-cell\@sm-only
     * .d-table-row\@sm-only
     */
}
@media (min-width: 48em) {
    /*
     * .d-block\@md
     * .d-flex\@md
     * .d-inline\@md
     * .d-inline-block\@md
     * .d-inline-flex\@md
     * .d-list-item\@md
     * .d-none\@md
     * .d-table\@md
     * .d-table-cell\@md
     * .d-table-row\@md
     */
}
@media (min-width: 48em) and (max-width: 63.99875em) {
    /*
     * .d-block\@md-only
     * .d-flex\@md-only
     * .d-inline\@md-only
     * .d-inline-block\@md-only
     * .d-inline-flex\@md-only
     * .d-list-item\@md-only
     * .d-none\@md-only
     * .d-table\@md-only
     * .d-table-cell\@md-only
     * .d-table-row\@md-only
     */
}
@media (min-width: 64em) {
    /*
     * .d-block\@lg
     * .d-flex\@lg
     * .d-inline\@lg
     * .d-inline-block\@lg
     * .d-inline-flex\@lg
     * .d-list-item\@lg
     * .d-none\@lg
     * .d-table\@lg
     * .d-table-cell\@lg
     * .d-table-row\@lg
     */
}
@media (min-width: 64em) and (max-width: 74.99875em) {
    /*
     * .d-block\@lg-only
     * .d-flex\@lg-only
     * .d-inline\@lg-only
     * .d-inline-block\@lg-only
     * .d-inline-flex\@lg-only
     * .d-list-item\@lg-only
     * .d-none\@lg-only
     * .d-table\@lg-only
     * .d-table-cell\@lg-only
     * .d-table-row\@lg-only
     */
}
@media (min-width: 75em) {
    /*
     * .d-block\@xl
     * .d-flex\@xl
     * .d-inline\@xl
     * .d-inline-block\@xl
     * .d-inline-flex\@xl
     * .d-list-item\@xl
     * .d-none\@xl
     * .d-table\@xl
     * .d-table-cell\@xl
     * .d-table-row\@xl
     */
}
@media (min-width: 75em) and (max-width: 99.99875em) {
    /*
     * .d-block\@xl-only
     * .d-flex\@xl-only
     * .d-inline\@xl-only
     * .d-inline-block\@xl-only
     * .d-inline-flex\@xl-only
     * .d-list-item\@xl-only
     * .d-none\@xl-only
     * .d-table\@xl-only
     * .d-table-cell\@xl-only
     * .d-table-row\@xl-only
     */
}
@media (min-width: 100em) {
    /*
     * .d-block\@xxl
     * .d-flex\@xxl
     * .d-inline\@xxl
     * .d-inline-block\@xxl
     * .d-inline-flex\@xxl
     * .d-list-item\@xxl
     * .d-none\@xxl
     * .d-table@xxl
     * .font-weight-bolder\@xxl
     * .font-weight-bolder\@xxl
     */
}
@media (min-width: 100em) {
    /*
     * .d-block\@xxl-only
     * .d-flex\@xxl-only
     * .d-inline\@xxl-only
     * .d-inline-block\@xxl-only
     * .d-inline-flex\@xxl-only
     * .d-list-item\@xxl-only
     * .d-none\@xxl-only
     * .d-table@xxl-only
     * .font-weight-bolder\@xxl-only
     * .font-weight-bolder\@xxl-only
     */
}
```

#### <a name="display-print-helper"></a>`display-print-helper()`

Set all display classes from the [`$displays`](#display-variables-displays) variable with print media query.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.display-print-helper;
```

##### Output
```css
@media print {
    /*
     * .d-block
     * .d-flex
     * .d-inline
     * .d-inline-block
     * .d-inline-flex
     * .d-list-item
     * .d-none
     * .d-table
     * .d-table-cell
     * .d-table-row
     */
}
```

#### <a name="display-screen-helper"></a>`display-screen-helper()`

Set all display classes from the [`$displays`](#display-variables-displays) variable with screen media query.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.display-screen-helper;
```

##### Output
```css
@media screen {
    /*
     * .d-block
     * .d-flex
     * .d-inline
     * .d-inline-block
     * .d-inline-flex
     * .d-list-item
     * .d-none
     * .d-table
     * .d-table-cell
     * .d-table-row
     */
}
```

#### <a name="display-display"></a>`display()`

Helper `display` entry point.  
Combine both [`display-helper`](#display-helper) and [`display-helper-with-bp`](#display-helper-with-bp) helpers in one helper.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.display;
// @include helpers.display(false);
```

##### Parameters
| Type | Description | Mandatory | Default |
|---|---|---|---|
| `Boolean` | Use `display-helper-with-bp()` | `false` | `true` |

##### Output
See [`display-helper`](#display-helper) and [`display-helper-with-bp`](#display-helper-with-bp) outputs.

<br />
<br />

## embed

- [Mixins](#embed-mixins)
  - [`embed-helper()`](#embed-helper)
  - [`embed-helper-with-bp()`](#embed-helper-with-bp)
  - [`embed()`](#embed-embed)

<br />

### <a name="embed-mixins"></a>Mixins

#### <a name="embed-helper"></a>`embed-helper()`

Create ratio-bound content blocks, to keep media (e.g. images, videos) in their correct aspect ratios.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.embed-helper;
```

##### Output
```css
.embed {
    display: block;
    position: relative;
    overflow: hidden;
}
.embed.-r1\:1::before {
    padding-bottom: 100%;
}
.embed.-r2\:1::before {
    padding-bottom: 50%;
}
.embed.-r3\:2::before {
    padding-bottom: 66.6666666667%;
}
.embed.-r4\:3::before {
    padding-bottom: 75%;
}
.embed.-r5\:3::before {
    padding-bottom: 60%;
}
.embed.-r5\:4::before {
    padding-bottom: 80%;
}
.embed.-r6\:5::before {
    padding-bottom: 83.3333333333%;
}
.embed.-r7\:3::before {
    padding-bottom: 42.8571428571%;
}
.embed.-r11\:8::before {
    padding-bottom: 72.7272727273%;
}
.embed.-r16\:9::before {
    padding-bottom: 56.25%;
}
.embed.-r16\:10::before {
    padding-bottom: 62.5%;
}
.embed::before {
    content: "";
    display: block;
    width: 100%;
    padding-bottom: 100%;
}
.embed_content,
.embed > iframe,
.embed > embed,
.embed > object,
.embed > video,
.embed > picture,
.embed > img {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    border: 0;
}
```

#### <a name="embed-helper-with-bp"></a>`embed-helper-with-bp()`

Create ratio-bound content blocks, to keep media (e.g. images, videos) in their correct aspect ratios with breakpoints media queries.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.embed-helper-with-bp;
```

##### Output
```css
@media (min-width: 20.375em) and (max-width: 35.99875em) {
    .embed.-r1\:1\@xs-only::before {
        padding-bottom: 100%;
    }
    .embed.-r2\:1\@xs-only::before {
        padding-bottom: 50%;
    }
    .embed.-r3\:2\@xs-only::before {
        padding-bottom: 66.6666666667%;
    }
    .embed.-r4\:3\@xs-only::before {
        padding-bottom: 75%;
    }
    .embed.-r5\:3\@xs-only::before {
        padding-bottom: 60%;
    }
    .embed.-r5\:4\@xs-only::before {
        padding-bottom: 80%;
    }
    .embed.-r6\:5\@xs-only::before {
        padding-bottom: 83.3333333333%;
    }
    .embed.-r7\:3\@xs-only::before {
        padding-bottom: 42.8571428571%;
    }
    .embed.-r11\:8\@xs-only::before {
        padding-bottom: 72.7272727273%;
    }
    .embed.-r16\:9\@xs-only::before {
        padding-bottom: 56.25%;
    }
    .embed.-r16\:10\@xs-only::before {
        padding-bottom: 62.5%;
    }
}
@media (min-width: 36em) {
 /*
  * .embed.-r1\:1\@sm::before
  * .embed.-r2\:1\@sm::before
  * .embed.-r3\:2\@sm::before
  * .embed.-r4\:3\@sm::before
  * .embed.-r5\:3\@sm::before
  * .embed.-r5\:4\@sm::before
  * .embed.-r6\:5\@sm::before
  * .embed.-r7\:3\@sm::before
  * .embed.-r11\:8\@sm::before
  * .embed.-r16\:9\@sm::before
  * .embed.-r16\:10\@sm::before
  */
}
@media (min-width: 36em) and (max-width: 47.99875em) {
 /*
  * .embed.-r1\:1\@sm-only::before
  * .embed.-r2\:1\@sm-only::before
  * .embed.-r3\:2\@sm-only::before
  * .embed.-r4\:3\@sm-only::before
  * .embed.-r5\:3\@sm-only::before
  * .embed.-r5\:4\@sm-only::before
  * .embed.-r6\:5\@sm-only::before
  * .embed.-r7\:3\@sm-only::before
  * .embed.-r11\:8\@sm-only::before
  * .embed.-r16\:9\@sm-only::before
  * .embed.-r16\:10\@sm-only::before
  */
}
@media (min-width: 48em) {
 /*
  * .embed.-r1\:1\@md::before
  * .embed.-r2\:1\@md::before
  * .embed.-r3\:2\@md::before
  * .embed.-r4\:3\@md::before
  * .embed.-r5\:3\@md::before
  * .embed.-r5\:4\@md::before
  * .embed.-r6\:5\@md::before
  * .embed.-r7\:3\@md::before
  * .embed.-r11\:8\@md::before
  * .embed.-r16\:9\@md::before
  * .embed.-r16\:10\@md::before
  */
}
@media (min-width: 48em) and (max-width: 63.99875em) {
 /*
  * .embed.-r1\:1\@md-only::before
  * .embed.-r2\:1\@md-only::before
  * .embed.-r3\:2\@md-only::before
  * .embed.-r4\:3\@md-only::before
  * .embed.-r5\:3\@md-only::before
  * .embed.-r5\:4\@md-only::before
  * .embed.-r6\:5\@md-only::before
  * .embed.-r7\:3\@md-only::before
  * .embed.-r11\:8\@md-only::before
  * .embed.-r16\:9\@md-only::before
  * .embed.-r16\:10\@md-only::before
  */
}
@media (min-width: 64em) {
 /*
  * .embed.-r1\:1\@lg::before
  * .embed.-r2\:1\@lg::before
  * .embed.-r3\:2\@lg::before
  * .embed.-r4\:3\@lg::before
  * .embed.-r5\:3\@lg::before
  * .embed.-r5\:4\@lg::before
  * .embed.-r6\:5\@lg::before
  * .embed.-r7\:3\@lg::before
  * .embed.-r11\:8\@lg::before
  * .embed.-r16\:9\@lg::before
  * .embed.-r16\:10\@lg::before
  */
}
@media (min-width: 64em) and (max-width: 74.99875em) {
 /*
  * .embed.-r1\:1\@lg-only::before
  * .embed.-r2\:1\@lg-only::before
  * .embed.-r3\:2\@lg-only::before
  * .embed.-r4\:3\@lg-only::before
  * .embed.-r5\:3\@lg-only::before
  * .embed.-r5\:4\@lg-only::before
  * .embed.-r6\:5\@lg-only::before
  * .embed.-r7\:3\@lg-only::before
  * .embed.-r11\:8\@lg-only::before
  * .embed.-r16\:9\@lg-only::before
  * .embed.-r16\:10\@lg-only::before
  */
}
@media (min-width: 75em) {
 /*
  * .embed.-r1\:1\@xl::before
  * .embed.-r2\:1\@xl::before
  * .embed.-r3\:2\@xl::before
  * .embed.-r4\:3\@xl::before
  * .embed.-r5\:3\@xl::before
  * .embed.-r5\:4\@xl::before
  * .embed.-r6\:5\@xl::before
  * .embed.-r7\:3\@xl::before
  * .embed.-r11\:8\@xl::before
  * .embed.-r16\:9\@xl::before
  * .embed.-r16\:10\@xl::before
  */
}
@media (min-width: 75em) and (max-width: 99.99875em) {
 /*
  * .embed.-r1\:1\@xl-only::before
  * .embed.-r2\:1\@xl-only::before
  * .embed.-r3\:2\@xl-only::before
  * .embed.-r4\:3\@xl-only::before
  * .embed.-r5\:3\@xl-only::before
  * .embed.-r5\:4\@xl-only::before
  * .embed.-r6\:5\@xl-only::before
  * .embed.-r7\:3\@xl-only::before
  * .embed.-r11\:8\@xl-only::before
  * .embed.-r16\:9\@xl-only::before
  * .embed.-r16\:10\@xl-only::before
  */
}
@media (min-width: 100em) {
 /*
  * .embed.-r1\:1\@xxl::before
  * .embed.-r2\:1\@xxl::before
  * .embed.-r3\:2\@xxl::before
  * .embed.-r4\:3\@xxl::before
  * .embed.-r5\:3\@xxl::before
  * .embed.-r5\:4\@xxl::before
  * .embed.-r6\:5\@xxl::before
  * .embed.-r7\:3\@xxl::before
  * .embed.-r11\:8\@xxl::before
  * .embed.-r16\:9\@xxl::before
  * .embed.-r16\:10\@xxl::before
  */
}
@media (min-width: 100em) {
 /*
  * .embed.-r1\:1\@xxl-only::before
  * .embed.-r2\:1\@xxl-only::before
  * .embed.-r3\:2\@xxl-only::before
  * .embed.-r4\:3\@xxl-only::before
  * .embed.-r5\:3\@xxl-only::before
  * .embed.-r5\:4\@xxl-only::before
  * .embed.-r6\:5\@xxl-only::before
  * .embed.-r7\:3\@xxl-only::before
  * .embed.-r11\:8\@xxl-only::before
  * .embed.-r16\:9\@xxl-only::before
  * .embed.-r16\:10\@xxl-only::before
  */
}
```

#### <a name="embed-embed"></a>`embed()`

Helper `embed` entry point.  
Combine both [`embed-helper`](#embed-helper) and [`embed-helper-with-bp`](#embed-helper-with-bp) helpers in one helper.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.embed;
// @include helpers.embed(false);
```

##### Parameters
| Type | Description | Mandatory | Default |
|---|---|---|---|
| `Boolean` | Use `embed-helper-with-bp()` | `false` | `true` |

##### Output
See [`embed-helper`](#embed-helper) and [`embed-helper-with-bp`](#embed-helper-with-bp) outputs.

<br />
<br />

## flexbox

- [Variables](#flexbox-variables)
  - [`$flexboxes`](#flexbox-variables-flexboxes)
  - [`$flexboxes-properties-class-override`](#flexbox-variables-flexboxes-properties-class-override)
  - [`$flexboxes-values-class-override`](#flexbox-variables-flexboxes-values-class-override)
  - [`$flexboxes-factors`](#flexbox-variables-flexboxes-factors)
  - [`$flexboxes-factors-max-loop`](#flexbox-variables-flexboxes-factors-max-loop)
  - [`$flexboxes-important`](#flexbox-variables-important)
- [Mixins](#flexbox-mixins)
  - [`flexbox-helper()`](#flexbox-helper)
  - [`flexbox-helper-with-bp()`](#flexbox-helper-with-bp)
  - [`flexbox-factor-helper()`](#flexbox-factor-helper)
  - [`flexbox-factor-helper-with-bp()`](#flexbox-factor-helper-with-bp)
  - [`flexbox()`](#flexbox-flexbox)

<br />

### <a name="flexbox-variables"></a>Variables

All those variables could be customized depending on what you need in your `variables.scss` file.  
Here are the default values.

#### <a name="flexbox-variables-flexboxes"></a>`$flexboxes`
Define all flexbox values to support.

```scss
$flexboxes: (
    'flex-direction': (
        row,
        row-reverse,
        column,
        column-reverse
    ),
    'flex-wrap': (
        wrap,
        nowrap,
        wrap-reverse
    ),
    'justify-content': (
        flex-start,
        flex-end,
        center,
        space-between,
        space-around
    ),
    'align-content': (
        flex-start,
        flex-end,
        center,
        space-between,
        space-around,
        stretch
    ),
    'align-items': (
        flex-start,
        flex-end,
        center,
        baseline,
        stretch
    ),
    'align-self': (
        flex-start,
        flex-end,
        center,
        baseline,
        stretch
    )
) !default;
```

#### <a name="flexbox-variables-flexboxes-properties-class-override"></a>`$flexboxes-properties-class-override`
Flexbox properties list for override class name.

```scss
$flexboxes-properties-class-override: (
    // 'flex-direction': '',
    // 'flex-wrap': '',
    // 'justify-content': '',
    // 'align-content': '',
    // 'align-items': '',
    // 'align-self': ''
) !default;
```

If you want to custom flexbox properties class name, just uncomment and set the value.  
For example, set `flex-direction` as `flex-d` will render:

```css
.flex-d-row {
  flex-direction: row !important;
}
```

#### <a name="flexbox-variables-flexboxes-values-class-override"></a>`$flexboxes-values-class-override`
Flexbox values list for override class name.

```scss
$flexboxes-values-class-override: (
    // 'row': '',
    // 'row-reverse': '',
    // 'column': '',
    // 'column-reverse': '',
    // 'wrap': '',
    // 'nowrap': '',
    // 'wrap-reverse': '',
    'flex-start': 'start',
    'flex-end': 'end',
    // 'center': '',
    // 'space-between': '',
    // 'space-around': '',
    // 'stretch': '',
    // 'baseline': ''
) !default;
```

If you want to custom flexbox values class name, just uncomment and set the value.  
By default, `flex-start` is set as `start`. Which will render:

```css
.justify-content-start {
    justify-content: flex-start !important;
}

/*
 * and not anymore
 *
 * .justify-content-flex-start { ... }
 *
 */
```

#### <a name="flexbox-variables-flexboxes-factors"></a>`$flexboxes-factors`
Flexbox factor properties to loop.  

> Note that the properties need to support only numeric value !

```scss
$flexboxes-factors: (
    'flex-grow',
    'flex-shrink',
    'order'
) !default;
```

#### <a name="flexbox-variables-flexboxes-factors-max-loop"></a>`$flexboxes-factors-max-loop`
Flexbox factor max loop.

```scss
$flexboxes-factors-max-loop: 12 !default;
```

#### <a name="flexbox-variables-important"></a>`$flexboxes-important`
Set the important property on each rules.

```scss
$flexboxes-important: true;
```

<br />

### <a name="flexbox-mixins"></a>Mixins

#### <a name="flexbox-helper"></a>`flexbox-helper()`

Set all flexbox classes from the [`$flexboxes`](flexbox-variables-flexboxes) variable.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.flexbox-helper;
```

##### Output
```css
.flex-direction-row {
    flex-direction: row !important;
}

.flex-direction-row-reverse {
    flex-direction: row-reverse !important;
}

.flex-direction-column {
    flex-direction: column !important;
}

.flex-direction-column-reverse {
    flex-direction: column-reverse !important;
}

.flex-wrap-wrap {
    flex-wrap: wrap !important;
}

.flex-wrap-nowrap {
    flex-wrap: nowrap !important;
}

.flex-wrap-wrap-reverse {
    flex-wrap: wrap-reverse !important;
}

.justify-content-start {
    justify-content: flex-start !important;
}

.justify-content-end {
    justify-content: flex-end !important;
}

.justify-content-center {
    justify-content: center !important;
}

.justify-content-space-between {
    justify-content: space-between !important;
}

.justify-content-space-around {
    justify-content: space-around !important;
}

.align-content-start {
    align-content: flex-start !important;
}

.align-content-end {
    align-content: flex-end !important;
}

.align-content-center {
    align-content: center !important;
}

.align-content-space-between {
    align-content: space-between !important;
}

.align-content-space-around {
    align-content: space-around !important;
}

.align-content-stretch {
    align-content: stretch !important;
}

.align-items-start {
    align-items: flex-start !important;
}

.align-items-end {
    align-items: flex-end !important;
}

.align-items-center {
    align-items: center !important;
}

.align-items-baseline {
    align-items: baseline !important;
}

.align-items-stretch {
    align-items: stretch !important;
}

.align-self-start {
    align-self: flex-start !important;
}

.align-self-end {
    align-self: flex-end !important;
}

.align-self-center {
    align-self: center !important;
}

.align-self-baseline {
    align-self: baseline !important;
}

.align-self-stretch {
    align-self: stretch !important;
}
```

#### <a name="flexbox-helper-with-bp"></a>`flexbox-helper-with-bp()`

Set all flexbox classes from the [`$flexboxes`](flexbox-variables-flexboxes) variable with breakpoints media queries.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.flexbox-helper-with-bp;
```

##### Output
```css
@media (min-width: 20.375em) and (max-width: 35.99875em) {
    .flex-direction-row\@xs-only {
        flex-direction: row !important;
    }

    .flex-direction-row-reverse\@xs-only {
        flex-direction: row-reverse !important;
    }

    .flex-direction-column\@xs-only {
        flex-direction: column !important;
    }

    .flex-direction-column-reverse\@xs-only {
        flex-direction: column-reverse !important;
    }

    .flex-wrap-wrap\@xs-only {
        flex-wrap: wrap !important;
    }

    .flex-wrap-nowrap\@xs-only {
        flex-wrap: nowrap !important;
    }

    .flex-wrap-wrap-reverse\@xs-only {
        flex-wrap: wrap-reverse !important;
    }

    .justify-content-start\@xs-only {
        justify-content: flex-start !important;
    }

    .justify-content-end\@xs-only {
        justify-content: flex-end !important;
    }

    .justify-content-center\@xs-only {
        justify-content: center !important;
    }

    .justify-content-space-between\@xs-only {
        justify-content: space-between !important;
    }

    .justify-content-space-around\@xs-only {
        justify-content: space-around !important;
    }

    .align-content-start\@xs-only {
        align-content: flex-start !important;
    }

    .align-content-end\@xs-only {
        align-content: flex-end !important;
    }

    .align-content-center\@xs-only {
        align-content: center !important;
    }

    .align-content-space-between\@xs-only {
        align-content: space-between !important;
    }

    .align-content-space-around\@xs-only {
        align-content: space-around !important;
    }

    .align-content-stretch\@xs-only {
        align-content: stretch !important;
    }

    .align-items-start\@xs-only {
        align-items: flex-start !important;
    }

    .align-items-end\@xs-only {
        align-items: flex-end !important;
    }

    .align-items-center\@xs-only {
        align-items: center !important;
    }

    .align-items-baseline\@xs-only {
        align-items: baseline !important;
    }

    .align-items-stretch\@xs-only {
        align-items: stretch !important;
    }

    .align-self-start\@xs-only {
        align-self: flex-start !important;
    }

    .align-self-end\@xs-only {
        align-self: flex-end !important;
    }

    .align-self-center\@xs-only {
        align-self: center !important;
    }

    .align-self-baseline\@xs-only {
        align-self: baseline !important;
    }

    .align-self-stretch\@xs-only {
        align-self: stretch !important;
    }
}
/* and so on */
@media (min-width: 36em) {
    /*
     * .flex-direction-row\@sm
     * .flex-direction-row-reverse\@sm
     * .flex-direction-column\@sm
     * .flex-direction-column-reverse\@sm
     * .flex-wrap-wrap\@sm
     * .flex-wrap-nowrap\@sm
     * .flex-wrap-wrap-reverse\@sm
     * .justify-content-start\@sm
     * .justify-content-end\@sm
     * .justify-content-center\@sm
     * .justify-content-space-between\@sm
     * .justify-content-space-around\@sm
     * .align-content-start\@sm
     * .align-content-end\@sm
     * .align-content-center\@sm
     * .align-content-space-between\@sm
     * .align-content-space-around\@sm
     * .align-content-stretch\@sm
     * .align-items-start\@sm
     * .align-items-end\@sm
     * .align-items-center\@sm
     * .align-items-baseline\@sm
     * .align-items-stretch\@sm
     * .align-self-start\@sm
     * .align-self-end\@sm
     * .align-self-center\@sm
     * .align-self-baseline\@sm
     * .align-self-stretch\@sm
     */
}
@media (min-width: 36em) and (max-width: 47.99875em) {
    /*
     * .flex-direction-row\@sm-only
     * .flex-direction-row-reverse\@sm-only
     * .flex-direction-column\@sm-only
     * .flex-direction-column-reverse\@sm-only
     * .flex-wrap-wrap\@sm-only
     * .flex-wrap-nowrap\@sm-only
     * .flex-wrap-wrap-reverse\@sm-only
     * .justify-content-start\@sm-only
     * .justify-content-end\@sm-only
     * .justify-content-center\@sm-only
     * .justify-content-space-between\@sm-only
     * .justify-content-space-around\@sm-only
     * .align-content-start\@sm-only
     * .align-content-end\@sm-only
     * .align-content-center\@sm-only
     * .align-content-space-between\@sm-only
     * .align-content-space-around\@sm-only
     * .align-content-stretch\@sm-only
     * .align-items-start\@sm-only
     * .align-items-end\@sm-only
     * .align-items-center\@sm-only
     * .align-items-baseline\@sm-only
     * .align-items-stretch\@sm-only
     * .align-self-start\@sm-only
     * .align-self-end\@sm-only
     * .align-self-center\@sm-only
     * .align-self-baseline\@sm-only
     * .align-self-stretch\@sm-only
     */
}
@media (min-width: 48em) {
    /*
     * .flex-direction-row\@md
     * .flex-direction-row-reverse\@md
     * .flex-direction-column\@md
     * .flex-direction-column-reverse\@md
     * .flex-wrap-wrap\@md
     * .flex-wrap-nowrap\@md
     * .flex-wrap-wrap-reverse\@md
     * .justify-content-start\@md
     * .justify-content-end\@md
     * .justify-content-center\@md
     * .justify-content-space-between\@md
     * .justify-content-space-around\@md
     * .align-content-start\@md
     * .align-content-end\@md
     * .align-content-center\@md
     * .align-content-space-between\@md
     * .align-content-space-around\@md
     * .align-content-stretch\@md
     * .align-items-start\@md
     * .align-items-end\@md
     * .align-items-center\@md
     * .align-items-baseline\@md
     * .align-items-stretch\@md
     * .align-self-start\@md
     * .align-self-end\@md
     * .align-self-center\@md
     * .align-self-baseline\@md
     * .align-self-stretch\@md
     */
}
@media (min-width: 48em) and (max-width: 63.99875em) {
    /*
     * .flex-direction-row\@md-only
     * .flex-direction-row-reverse\@md-only
     * .flex-direction-column\@md-only
     * .flex-direction-column-reverse\@md-only
     * .flex-wrap-wrap\@md-only
     * .flex-wrap-nowrap\@md-only
     * .flex-wrap-wrap-reverse\@md-only
     * .justify-content-start\@md-only
     * .justify-content-end\@md-only
     * .justify-content-center\@md-only
     * .justify-content-space-between\@md-only
     * .justify-content-space-around\@md-only
     * .align-content-start\@md-only
     * .align-content-end\@md-only
     * .align-content-center\@md-only
     * .align-content-space-between\@md-only
     * .align-content-space-around\@md-only
     * .align-content-stretch\@md-only
     * .align-items-start\@md-only
     * .align-items-end\@md-only
     * .align-items-center\@md-only
     * .align-items-baseline\@md-only
     * .align-items-stretch\@md-only
     * .align-self-start\@md-only
     * .align-self-end\@md-only
     * .align-self-center\@md-only
     * .align-self-baseline\@md-only
     * .align-self-stretch\@md-only
     */
}
@media (min-width: 64em) {
    /*
     * .flex-direction-row\@lg
     * .flex-direction-row-reverse\@lg
     * .flex-direction-column\@lg
     * .flex-direction-column-reverse\@lg
     * .flex-wrap-wrap\@lg
     * .flex-wrap-nowrap\@lg
     * .flex-wrap-wrap-reverse\@lg
     * .justify-content-start\@lg
     * .justify-content-end\@lg
     * .justify-content-center\@lg
     * .justify-content-space-between\@lg
     * .justify-content-space-around\@lg
     * .align-content-start\@lg
     * .align-content-end\@lg
     * .align-content-center\@lg
     * .align-content-space-between\@lg
     * .align-content-space-around\@lg
     * .align-content-stretch\@lg
     * .align-items-start\@lg
     * .align-items-end\@lg
     * .align-items-center\@lg
     * .align-items-baseline\@lg
     * .align-items-stretch\@lg
     * .align-self-start\@lg
     * .align-self-end\@lg
     * .align-self-center\@lg
     * .align-self-baseline\@lg
     * .align-self-stretch\@lg
     */
}
@media (min-width: 64em) and (max-width: 74.99875em) {
    /*
     * .flex-direction-row\@lg-only
     * .flex-direction-row-reverse\@lg-only
     * .flex-direction-column\@lg-only
     * .flex-direction-column-reverse\@lg-only
     * .flex-wrap-wrap\@lg-only
     * .flex-wrap-nowrap\@lg-only
     * .flex-wrap-wrap-reverse\@lg-only
     * .justify-content-start\@lg-only
     * .justify-content-end\@lg-only
     * .justify-content-center\@lg-only
     * .justify-content-space-between\@lg-only
     * .justify-content-space-around\@lg-only
     * .align-content-start\@lg-only
     * .align-content-end\@lg-only
     * .align-content-center\@lg-only
     * .align-content-space-between\@lg-only
     * .align-content-space-around\@lg-only
     * .align-content-stretch\@lg-only
     * .align-items-start\@lg-only
     * .align-items-end\@lg-only
     * .align-items-center\@lg-only
     * .align-items-baseline\@lg-only
     * .align-items-stretch\@lg-only
     * .align-self-start\@lg-only
     * .align-self-end\@lg-only
     * .align-self-center\@lg-only
     * .align-self-baseline\@lg-only
     * .align-self-stretch\@lg-only
     */
}
@media (min-width: 75em) {
    /*
     * .flex-direction-row\@xl
     * .flex-direction-row-reverse\@xl
     * .flex-direction-column\@xl
     * .flex-direction-column-reverse\@xl
     * .flex-wrap-wrap\@xl
     * .flex-wrap-nowrap\@xl
     * .flex-wrap-wrap-reverse\@xl
     * .justify-content-start\@xl
     * .justify-content-end\@xl
     * .justify-content-center\@xl
     * .justify-content-space-between\@xl
     * .justify-content-space-around\@xl
     * .align-content-start\@xl
     * .align-content-end\@xl
     * .align-content-center\@xl
     * .align-content-space-between\@xl
     * .align-content-space-around\@xl
     * .align-content-stretch\@xl
     * .align-items-start\@xl
     * .align-items-end\@xl
     * .align-items-center\@xl
     * .align-items-baseline\@xl
     * .align-items-stretch\@xl
     * .align-self-start\@xl
     * .align-self-end\@xl
     * .align-self-center\@xl
     * .align-self-baseline\@xl
     * .align-self-stretch\@xl
     */
}
@media (min-width: 75em) and (max-width: 99.99875em) {
    /*
     * .flex-direction-row\@xl-only
     * .flex-direction-row-reverse\@xl-only
     * .flex-direction-column\@xl-only
     * .flex-direction-column-reverse\@xl-only
     * .flex-wrap-wrap\@xl-only
     * .flex-wrap-nowrap\@xl-only
     * .flex-wrap-wrap-reverse\@xl-only
     * .justify-content-start\@xl-only
     * .justify-content-end\@xl-only
     * .justify-content-center\@xl-only
     * .justify-content-space-between\@xl-only
     * .justify-content-space-around\@xl-only
     * .align-content-start\@xl-only
     * .align-content-end\@xl-only
     * .align-content-center\@xl-only
     * .align-content-space-between\@xl-only
     * .align-content-space-around\@xl-only
     * .align-content-stretch\@xl-only
     * .align-items-start\@xl-only
     * .align-items-end\@xl-only
     * .align-items-center\@xl-only
     * .align-items-baseline\@xl-only
     * .align-items-stretch\@xl-only
     * .align-self-start\@xl-only
     * .align-self-end\@xl-only
     * .align-self-center\@xl-only
     * .align-self-baseline\@xl-only
     * .align-self-stretch\@xl-only
     */
}
@media (min-width: 100em) {
    /*
     * .flex-direction-row\@xxl
     * .flex-direction-row-reverse\@xxl
     * .flex-direction-column\@xxl
     * .flex-direction-column-reverse\@xxl
     * .flex-wrap-wrap\@xxl
     * .flex-wrap-nowrap\@xxl
     * .flex-wrap-wrap-reverse\@xxl
     * .justify-content-start\@xxl
     * .justify-content-end\@xxl
     * .justify-content-center\@xxl
     * .justify-content-space-between\@xxl
     * .justify-content-space-around\@xxl
     * .align-content-start\@xxl
     * .align-content-end\@xxl
     * .align-content-center\@xxl
     * .align-content-space-between\@xxl
     * .align-content-space-around\@xxl
     * .align-content-stretch\@xxl
     * .align-items-start\@xxl
     * .align-items-end\@xxl
     * .align-items-center\@xxl
     * .align-items-baseline\@xxl
     * .align-items-stretch\@xxl
     * .align-self-start\@xxl
     * .align-self-end\@xxl
     * .align-self-center\@xxl
     * .align-self-baseline\@xxl
     * .align-self-stretch\@xxl
     */
}
@media (min-width: 100em) {
    /*
     * .flex-direction-row\@xxl-only
     * .flex-direction-row-reverse\@xxl-only
     * .flex-direction-column\@xxl-only
     * .flex-direction-column-reverse\@xxl-only
     * .flex-wrap-wrap\@xxl-only
     * .flex-wrap-nowrap\@xxl-only
     * .flex-wrap-wrap-reverse\@xxl-only
     * .justify-content-start\@xxl-only
     * .justify-content-end\@xxl-only
     * .justify-content-center\@xxl-only
     * .justify-content-space-between\@xxl-only
     * .justify-content-space-around\@xxl-only
     * .align-content-start\@xxl-only
     * .align-content-end\@xxl-only
     * .align-content-center\@xxl-only
     * .align-content-space-between\@xxl-only
     * .align-content-space-around\@xxl-only
     * .align-content-stretch\@xxl-only
     * .align-items-start\@xxl-only
     * .align-items-end\@xxl-only
     * .align-items-center\@xxl-only
     * .align-items-baseline\@xxl-only
     * .align-items-stretch\@xxl-only
     * .align-self-start\@xxl-only
     * .align-self-end\@xxl-only
     * .align-self-center\@xxl-only
     * .align-self-baseline\@xxl-only
     * .align-self-stretch\@xxl-only
     */
}
```

#### <a name="flexbox-factor-helper"></a>`flexbox-factor-helper()`

Loop with [`$flexboxes-factors-max-loop`](flexbox-variables-flexboxes-factors-max-loop) variable to set all flexbox factor classes from the [`$flexboxes-factors`](flexbox-variables-flexboxes-factors) variable.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.flexbox-factor-helper;
```

##### Output
```css
.flex-grow-0 {
    flex-grow: 0 !important;
}
.flex-grow-1 {
    flex-grow: 1 !important;
}
/*
 * and so on until the value set to `$flexboxes-factors-max-loop`
 */

.flex-shrink-0 {
    flex-shrink: 0 !important;
}
.flex-shrink-1 {
    flex-shrink: 1 !important;
}
/*
 * and so on until the value set to `$flexboxes-factors-max-loop`
 */

.order-0 {
    order: 0 !important;
}
.order-1 {
    order: 1 !important;
}
/*
 * and so on until the value set to `$flexboxes-factors-max-loop`
 */
```

#### <a name="flexbox-factor-helper-with-bp"></a>`flexbox-factor-helper-with-bp()`

Loop with [`$flexboxes-factors-max-loop`](flexbox-variables-flexboxes-factors-max-loop) variable to set all flexbox factor classes from the [`$flexboxes-factors`](flexbox-variables-flexboxes-factors) variable with breakpoints media queries.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.flexbox-factor-helper;
```

##### Output
```css
@media (min-width: 20.375em) and (max-width: 35.99875em) {
    .flex-grow-0\@xs-only {
        flex-grow: 0 !important;
    }
    .flex-grow-1\@xs-only {
        flex-grow: 1 !important;
    }
    /*
    * and so on until the value set to `$flexboxes-factors-max-loop`
    */

    .flex-shrink-0\@xs-only {
        flex-shrink: 0 !important;
    }
    .flex-shrink-1\@xs-only {
        flex-shrink: 1 !important;
    }
    /*
    * and so on until the value set to `$flexboxes-factors-max-loop`
    */

    .order-0\@xs-only {
        order: 0 !important;
    }
    .order-1\@xs-only {
        order: 1 !important;
    }
    /*
    * and so on until the value set to `$flexboxes-factors-max-loop`
    */
}
/* and so on */
@media (min-width: 36em) {
    /*
     * .flex-grow-0\@sm
     * .flex-grow-1\@sm
     * ...
     * .flex-shrink-0\@sm
     * .flex-shrink-1\@sm
     * ...
     * .order-0\@sm
     * .order-1\@sm
     * ...
     */
}
@media (min-width: 36em) and (max-width: 47.99875em) {
    /*
     * .flex-grow-0\@sm-only
     * .flex-grow-1\@sm-only
     * ...
     * .flex-shrink-0\@sm-only
     * .flex-shrink-1\@sm-only
     * ...
     * .order-0\@sm-only
     * .order-1\@sm-only
     * ...
     */
}
@media (min-width: 48em) {
    /*
     * .flex-grow-0\@md
     * .flex-grow-1\@md
     * ...
     * .flex-shrink-0\@md
     * .flex-shrink-1\@md
     * ...
     * .order-0\@md
     * .order-1\@md
     * ...
     */
}
@media (min-width: 48em) and (max-width: 63.99875em) {
    /*
     * .flex-grow-0\@md-only
     * .flex-grow-1\@md-only
     * ...
     * .flex-shrink-0\@md-only
     * .flex-shrink-1\@md-only
     * ...
     * .order-0\@md-only
     * .order-1\@md-only
     * ...
     */
}
@media (min-width: 64em) {
    /*
     * .flex-grow-0\@lg
     * .flex-grow-1\@lg
     * ...
     * .flex-shrink-0\@lg
     * .flex-shrink-1\@lg
     * ...
     * .order-0\@lg
     * .order-1\@lg
     * ...
     */
}
@media (min-width: 64em) and (max-width: 74.99875em) {
    /*
     * .flex-grow-0\@lg-only
     * .flex-grow-1\@lg-only
     * ...
     * .flex-shrink-0\@lg-only
     * .flex-shrink-1\@lg-only
     * ...
     * .order-0\@lg-only
     * .order-1\@lg-only
     * ...
     */
}
@media (min-width: 75em) {
    /*
     * .flex-grow-0\@xl
     * .flex-grow-1\@xl
     * ...
     * .flex-shrink-0\@xl
     * .flex-shrink-1\@xl
     * ...
     * .order-0\@xl
     * .order-1\@xl
     * ...
     */
}
@media (min-width: 75em) and (max-width: 99.99875em) {
    /*
     * .flex-grow-0\@xl-only
     * .flex-grow-1\@xl-only
     * ...
     * .flex-shrink-0\@xl-only
     * .flex-shrink-1\@xl-only
     * ...
     * .order-0\@xl-only
     * .order-1\@xl-only
     * ...
     */
}
@media (min-width: 100em) {
    /*
     * .flex-grow-0\@xxl
     * .flex-grow-1\@xxl
     * ...
     * .flex-shrink-0\@xxl
     * .flex-shrink-1\@xxl
     * ...
     * .order-0\@xxl
     * .order-1\@xxl
     * ...
     */
}
@media (min-width: 100em) {
    /*
     * .flex-grow-0\@xxl-only
     * .flex-grow-1\@xxl-only
     * ...
     * .flex-shrink-0\@xxl-only
     * .flex-shrink-1\@xxl-only
     * ...
     * .order-0\@xxl-only
     * .order-1\@xxl-only
     * ...
     */
}
```

#### <a name="flexbox-flexbox"></a>`flexbox()`

Helper `flexbox` entry point.  
Combine [`flexbox-helper`](#flexbox-helper), [`flexbox-helper-with-bp`](#flexbox-helper-with-bp), [`flexbox-factor`](#flexbox-factor) and [`flexbox-factor-with-bp`](#flexbox-factor-with-bp) helpers in one helper.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.flexbox;
// @include helpers.flexbox(false);
```

##### Parameters
| Type | Description | Mandatory | Default |
|---|---|---|---|
| `Boolean` | Use `flexbox-helper-with-bp()` | `false` | `true` |

##### Output
See [`flexbox-helper`](#flexbox-helper), [`flexbox-helper-with-bp`](#flexbox-helper-with-bp), [`flexbox-factor`](#flexbox-factor) and [`flexbox-factor-with-bp`](#flexbox-factor-with-bp) outputs.

<br />
<br />

## float

- [Variables](#float-variables)
  - [`$floats`](#float-variables-floats)
- [Mixins](#float-mixins)
  - [`float-helper()`](#float-helper)
  - [`float-helper-with-bp()`](#float-helper-with-bp)
  - [`float()`](#float-float)

<br />

### <a name="float-variables"></a>Variables

This variable could be customized depending on what you need in your `variables.scss` file.  
Here is the default value.

#### <a name="float-variables-floats"></a>`$floats`
Define all float values to support.

```scss
$floats: (
    right,
    left,
    none
) !default;
```

<br />

### <a name="float-mixins"></a>Mixins

#### <a name="float-helper"></a>`float-helper()`

Set all float classes from the [`$floats`](#float-variables-floats) variable.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.float-helper;
```

##### Output
```css
.float-right {
    float: right !important;
}

.float-left {
    float: left !important;
}

.float-none {
    float: none !important;
}
```

#### <a name="float-helper-with-bp"></a>`float-helper-with-bp()`

Set all float classes from the [`$floats`](#float-variables-floats) variable with breakpoints media queries.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.float-helper-with-bp;
```

##### Output
```css
@media (min-width: 20.375em) and (max-width: 35.99875em) {
    .float-right\@xs-only {
        float: right !important;
    }

    .float-left\@xs-only {
        float: left !important;
    }

    .float-none\@xs-only {
        float: none !important;
    }
}
/* and so on */
@media (min-width: 36em) {
    /*
     * .float-right\@sm
     * .float-left\@sm
     * .float-none\@sm
     */
}
@media (min-width: 36em) and (max-width: 47.99875em) {
    /*
     * .float-right\@sm-only
     * .float-left\@sm-only
     * .float-none\@sm-only
     */
}
@media (min-width: 48em) {
    /*
     * .float-right\@md
     * .float-left\@md
     * .float-none\@md
     */
}
@media (min-width: 48em) and (max-width: 63.99875em) {
    /*
     * .float-right\@md-only
     * .float-left\@md-only
     * .float-none\@md-only
     */
}
@media (min-width: 64em) {
    /*
     * .float-right\@lg
     * .float-left\@lg
     * .float-none\@lg
     */
}
@media (min-width: 64em) and (max-width: 74.99875em) {
    /*
     * .float-right\@lg-only
     * .float-left\@lg-only
     * .float-none\@lg-only
     */
}
@media (min-width: 75em) {
    /*
     * .float-right\@xl
     * .float-left\@xl
     * .float-none\@xl
     */
}
@media (min-width: 75em) and (max-width: 99.99875em) {
    /*
     * .float-right\@xl-only
     * .float-left\@xl-only
     * .float-none\@xl-only
     */
}
@media (min-width: 100em) {
    /*
     * .float-right\@xxl
     * .float-left\@xxl
     * .float-none\@xxl
     */
}
@media (min-width: 100em) {
    /*
     * .float-right\@xxl-only
     * .float-left\@xxl-only
     * .float-none\@xxl-only
     */
}
```

#### <a name="float-float"></a>`float()`

Helper `float` entry point.  
Combine both [`float-helper`](#float-helper) and [`float-helper-with-bp`](#float-helper-with-bp) helpers in one helper.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.float;
// @include helpers.float(false);
```

##### Parameters
| Type | Description | Mandatory | Default |
|---|---|---|---|
| `Boolean` | Use `float-helper-with-bp()` | `false` | `true` |

##### Output
See [`float-helper()`](#float-helper) and [`float-helper-with-bp()`](#float-helper-with-bp) outputs.

<br />
<br />

## font

- [Variables](#font-variables)
  - [`$fonts-style`](#font-variables-fonts-style)
  - [`$fonts-weight`](#font-variables-fonts-weight)
  - [`$fonts-important`](#font-variables-fonts-important)
- [Mixins](#font-mixins)
  - [`font-style-helper()`](#font-style-helper)
  - [`font-weight-helper()`](#font-weight-helper)
  - [`font-helper-with-bp()`](#font-helper-with-bp)
  - [`font()`](#font-font)

<br />

### <a name="font-variables"></a>Variables

Those variables could be customized depending on what you need in your `variables.scss` file.  
Here are the default values.

#### <a name="font-variables-fonts-style"></a>`$fonts-style`
Define all font-style values to support.

```scss
$fonts-style: (
    italic: 'italic'
) !default;
```

#### <a name="font-variables-fonts-weight"></a>`$fonts-weight`
Define all font-weight values to support.

```scss
$fonts-weight: (
    lighter: 100,
    light: 200,
    normal: 300,
    bold: 600,
    bolder: 800
) !default;
```

#### <a name="font-variables-fonts-important"></a>`$fonts-important`
Set the important property on each rules.

```scss
$fonts-important: true;
```

<br />

### <a name="font-mixins"></a>Mixins

#### <a name="font-style-helper"></a>`font-style-helper()`

Set all font style classes from the [`$fonts-style`](#font-variables-fonts-style) variable.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.font-style-helper;
```

##### Output
```css
.font-weight-italic {
    font-style: "italic" !important;
}
```

#### <a name="font-weight-helper"></a>`font-weight-helper()`

Set all font weight classes from the [`$fonts-weight`](#font-variables-fonts-weight) variable.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.font-weight-helper;
```

##### Output
```css
.font-weight-lighter {
    font-weight: 100 !important;
}

.font-weight-light {
    font-weight: 200 !important;
}

.font-weight-normal {
    font-weight: 300 !important;
}

.font-weight-bold {
    font-weight: 600 !important;
}

.font-weight-bolder {
    font-weight: 800 !important;
}
```

#### <a name="font-helper-with-bp"></a>`font-helper-with-bp()`

Set all font style classes from the [`$fonts-style`](#font-variables-fonts-style) variable and all font weight classes from the [`$fonts-weight`](#font-variables-fonts-weight) variable with breakpoints media queries.


```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.font-helper-with-bp;
```

##### Output
```css
@media (min-width: 20.375em) and (max-width: 35.99875em) {
    .font-weight-italic\@xs-only {
        font-style: "italic" !important;
    }

    .font-weight-lighter\@xs-only {
        font-weight: 100 !important;
    }

    .font-weight-light\@xs-only {
        font-weight: 200 !important;
    }

    .font-weight-normal\@xs-only {
        font-weight: 300 !important;
    }

    .font-weight-bold\@xs-only {
        font-weight: 600 !important;
    }

    .font-weight-bolder\@xs-only {
        font-weight: 800 !important;
    }
}
/* and so on */
@media (min-width: 36em) {
    /*
     * .font-weight-italic\@sm
     * .font-weight-lighter\@sm
     * .font-weight-light\@sm
     * .font-weight-normal\@sm
     * .font-weight-bold\@sm
     * .font-weight-bolder\@sm
     */
}
@media (min-width: 36em) and (max-width: 47.99875em) {
    /*
     * .font-weight-italic\@sm-only
     * .font-weight-lighter\@sm-only
     * .font-weight-light\@sm-only
     * .font-weight-light\@sm-only
     * .font-weight-bold\@sm-only
     * .font-weight-bolder\@sm-only
     */
}
@media (min-width: 48em) {
    /*
     * .font-weight-italic\@md
     * .font-weight-lighter\@md
     * .font-weight-light\@md
     * .font-weight-normal\@md
     * .font-weight-bold\@md
     * .font-weight-bolder\@md
     */
}
@media (min-width: 48em) and (max-width: 63.99875em) {
    /*
     * .font-weight-italic\@md-only
     * .font-weight-lighter\@md-only
     * .font-weight-light\@md-only
     * .font-weight-light\@md-only
     * .font-weight-bold\@md-only
     * .font-weight-bolder\@md-only
     */
}
@media (min-width: 64em) {
    /*
     * .font-weight-italic\@lg
     * .font-weight-lighter\@lg
     * .font-weight-light\@lg
     * .font-weight-normal\@lg
     * .font-weight-bold\@lg
     * .font-weight-bolder\@lg
     */
}
@media (min-width: 64em) and (max-width: 74.99875em) {
    /*
     * .font-weight-italic\@lg-only
     * .font-weight-lighter\@lg-only
     * .font-weight-light\@lg-only
     * .font-weight-light\@lg-only
     * .font-weight-bold\@lg-only
     * .font-weight-bolder\@lg-only
     */
}
@media (min-width: 75em) {
    /*
     * .font-weight-italic\@xl
     * .font-weight-lighter\@xl
     * .font-weight-light\@xl
     * .font-weight-normal\@xl
     * .font-weight-bold\@xl
     * .font-weight-bolder\@xl
     */
}
@media (min-width: 75em) and (max-width: 99.99875em) {
    /*
     * .font-weight-italic\@xl-only
     * .font-weight-lighter\@xl-only
     * .font-weight-light\@xl-only
     * .font-weight-light\@xl-only
     * .font-weight-bold\@xl-only
     * .font-weight-bolder\@xl-only
     */
}
@media (min-width: 100em) {
    /*
     * .font-weight-italic\@xxl
     * .font-weight-lighter\@xxl
     * .font-weight-light\@xxl
     * .font-weight-normal\@xxl
     * .font-weight-bold\@xxl
     * .font-weight-bolder\@xxl
     */
}
@media (min-width: 100em) {
    /*
     * .font-weight-italic\@xxl-only
     * .font-weight-lighter\@xxl-only
     * .font-weight-light\@xxl-only
     * .font-weight-light\@xxl-only
     * .font-weight-bold\@xxl-only
     * .font-weight-bolder\@xxl-only
     */
}
```

#### <a name="font-font"></a>`font()`

Helper `font` entry point.  
Combine [`font-style-helper`](#font-style-helper), [`font-weight-helper`](#font-weight-helper) and [`font-helper-with-bp`](#font-helper-with-bp) helpers in one helper.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.font;
// @include helpers.font(false);
```

##### Parameters
| Type | Description | Mandatory | Default |
|---|---|---|---|
| `Boolean` | Use `font-helper-with-bp()` | `false` | `true` |

##### Output
See [`font-style-helper`](#font-style-helper), [`font-weight-helper`](#font-weight-helper) and [`font-helper-with-bp`](#font-helper-with-bp) outputs.

<br />
<br />

## overflow

- [Variables](#overflow-variables)
  - [`$overflows`](#overflow-variables-overflows)
- [Mixins](#overflow-mixins)
  - [`overflow-helper()`](#overflow-helper)
  - [`overflow-helper-with-bp()`](#overflow-helper-with-bp)
  - [`overflow()`](#overflow-overflow)

<br />

### <a name="overflow-variables"></a>Variables

This variable could be customized depending on what you need in your `variables.scss` file.  
Here is the default value.

#### <a name="overflow-variables-overflows"></a>`$overflows`
Define all position values to support.

```scss
$overflows: (
    auto,
    hidden
) !default;
```

<br />

### <a name="overflow-mixins"></a>Mixins

#### <a name="overflow-helper"></a>`overflow-helper()`

Set all float classes from the [`$overflows`](#overflow-variables-overflows) variable.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.overflow-helper;
```

##### Output
```css
.overflow-auto {
    overflow: auto !important;
}

.overflow-hidden {
    overflow: hidden !important;
}
```

#### <a name="overflow-helper-with-bp"></a>`overflow-helper-with-bp()`

Set all float classes from the [`$overflows`](#overflow-variables-overflows) variable with breakpoints media queries.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.overflow-helper-with-bp;
```

##### Output
```css
@media (min-width: 20.375em) and (max-width: 35.99875em) {
    .overflow-auto\@xs-only {
        overflow: auto !important;
    }

    .overflow-hidden\@xs-only {
        overflow: hidden !important;
    }
}
/* and so on */
@media (min-width: 36em) {
    /*
     * .overflow-auto\@sm
     * .overflow-hidden\@sm
     */
}
@media (min-width: 36em) and (max-width: 47.99875em) {
    /*
     * .overflow-auto\@sm-only
     * .overflow-hidden\@sm-only
     */
}
@media (min-width: 48em) {
    /*
     * .overflow-auto\@md
     * .overflow-hidden\@md
     */
}
@media (min-width: 48em) and (max-width: 63.99875em) {
    /*
     * .overflow-auto\@md-only
     * .overflow-hidden\@md-only
     */
}
@media (min-width: 64em) {
    /*
     * .overflow-auto\@lg
     * .overflow-hidden\@lg
     */
}
@media (min-width: 64em) and (max-width: 74.99875em) {
    /*
     * .overflow-auto\@lg-only
     * .overflow-hidden\@lg-only
     */
}
@media (min-width: 75em) {
    /*
     * .overflow-auto\@xl
     * .overflow-hidden\@xl
     */
}
@media (min-width: 75em) and (max-width: 99.99875em) {
    /*
     * .overflow-auto\@xl-only
     * .overflow-hidden\@xl-only
     */
}
@media (min-width: 100em) {
    /*
     * .overflow-auto\@xxl
     * .overflow-hidden\@xxl
     */
}
@media (min-width: 100em) {
    /*
     * .overflow-auto\@xxl-only
     * .overflow-hidden\@xxl-only
     */
}
```

#### <a name="overflow-overflow"></a>`overflow()`

Helper `overflow` entry point.  
Combine both [`overflow-helper`](#overflow-helper) and [`overflow-helper-with-bp`](#overflow-helper-with-bp) helpers in one helper.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.overflow;
// @include helpers.overflow(false);
```

##### Parameters
| Type | Description | Mandatory | Default |
|---|---|---|---|
| `Boolean` | Use `overflow-helper-with-bp()` | `false` | `true` |

##### Output
See [`overflow-helper()`](#overflow-helper) and [`overflow-helper-with-bp()`](#overflow-helper-with-bp) outputs.

<br />
<br />

## position

- [Variables](#position-variables)
  - [`$positions`](#position-variables-positions)
- [Mixins](#position-mixins)
  - [`position-helper()`](#position-helper)
  - [`position-helper-with-bp()`](#position-helper-with-bp)
  - [`position()`](#position-position)

<br />

### <a name="position-variables"></a>Variables

This variable could be customized depending on what you need in your `variables.scss` file.  
Here is the default value.

#### <a name="position-variables-positions"></a>`$positions`
Define all position values to support.

```scss
$positions: (
    absolute,
    fixed,
    initial,
    inherit,
    relative,
    static
) !default;
```

<br />

### <a name="position-mixins"></a>Mixins

#### <a name="position-helper"></a>`position-helper()`

Set all position classes from the [`$positions`](#position-variables-positions) variable.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.position-helper;
```

##### Output
```css
.position-absolute {
    position: absolute !important;
}

.position-fixed {
    position: fixed !important;
}

.position-initial {
    position: initial !important;
}

.position-inherit {
    position: inherit !important;
}

.position-relative {
    position: relative !important;
}

.position-static {
    position: static !important;
}

.fixed-top,
.fixed-bottom {
    left: 0;
    position: fixed;
    right: 0;
}
.fixed-top {
    top: 0;
}
.fixed-bottom {
    bottom: 0;
}
```

#### <a name="position-helper-with-bp"></a>`position-helper-with-bp()`

Set all position classes from the [`$positions`](#position-variables-positions) variable with breakpoints media queries.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.position-helper-with-bp;
```

##### Output
```css
@media (min-width: 20.375em) and (max-width: 35.99875em) {
    .position-absolute\@xs-only {
        position: absolute !important;
    }

    .position-fixed\@xs-only {
        position: fixed !important;
    }

    .position-initial\@xs-only {
        position: initial !important;
    }

    .position-inherit\@xs-only {
        position: inherit !important;
    }

    .position-relative\@xs-only {
        position: relative !important;
    }

    .position-static\@xs-only {
        position: static !important;
    }

    .fixed-top\@xs-only,
    .fixed-bottom\@xs-only {
        left: 0;
        position: fixed;
        right: 0;
    }
    .fixed-top\@xs-only {
        top: 0;
    }
    .fixed-bottom\@xs-only {
        bottom: 0;
    }
}
/* and so on */
@media (min-width: 36em) {
    /*
     * .position-absolute\@sm
     * .position-fixed\@sm
     * .position-initial\@sm
     * .position-inherit\@sm
     * .position-relative\@sm
     * .position-static\@sm
     * .fixed-top\@sm
     * .fixed-bottom\@sm
     */
}
@media (min-width: 36em) and (max-width: 47.99875em) {
    /*
     * .position-absolute\@sm-only
     * .position-fixed\@sm-only
     * .position-initial\@sm-only
     * .position-inherit\@sm-only
     * .position-relative\@sm-only
     * .position-static\@sm-only
     * .fixed-top\@sm-only
     * .fixed-bottom\@sm-only
     */
}
@media (min-width: 48em) {
    /*
     * .position-absolute\@md
     * .position-fixed\@md
     * .position-initial\@md
     * .position-inherit\@md
     * .position-relative\@md
     * .position-static\@md
     * .fixed-top\@md
     * .fixed-bottom\@md
     */
}
@media (min-width: 48em) and (max-width: 63.99875em) {
    /*
     * .position-absolute\@md-only
     * .position-fixed\@md-only
     * .position-initial\@md-only
     * .position-inherit\@md-only
     * .position-relative\@md-only
     * .position-static\@md-only
     * .fixed-top\@md-only
     * .fixed-bottom\@md-only
     */
}
@media (min-width: 64em) {
    /*
     * .position-absolute\@lg
     * .position-fixed\@lg
     * .position-initial\@lg
     * .position-inherit\@lg
     * .position-relative\@lg
     * .position-static\@lg
     * .fixed-top\@lg
     * .fixed-bottom\@lg
     */
}
@media (min-width: 64em) and (max-width: 74.99875em) {
    /*
     * .position-absolute\@lg-only
     * .position-fixed\@lg-only
     * .position-initial\@lg-only
     * .position-inherit\@lg-only
     * .position-relative\@lg-only
     * .position-static\@lg-only
     * .fixed-top\@lg-only
     * .fixed-bottom\@lg-only
     */
}
@media (min-width: 75em) {
    /*
     * .position-absolute\@xl
     * .position-fixed\@xl
     * .position-initial\@xl
     * .position-inherit\@xl
     * .position-relative\@xl
     * .position-static\@xl
     * .fixed-top\@xl
     * .fixed-bottom\@xl
     */
}
@media (min-width: 75em) and (max-width: 99.99875em) {
    /*
     * .position-absolute\@xl-only
     * .position-fixed\@xl-only
     * .position-initial\@xl-only
     * .position-inherit\@xl-only
     * .position-relative\@xl-only
     * .position-static\@xl-only
     * .fixed-top\@xl-only
     * .fixed-bottom\@xl-only
     */
}
@media (min-width: 100em) {
    /*
     * .position-absolute\@xxl
     * .position-fixed\@xxl
     * .position-initial\@xxl
     * .position-inherit\@xxl
     * .position-relative\@xxl
     * .position-static\@xxl
     * .fixed-top\@xxl
     * .fixed-bottom\@xxl
     */
}
@media (min-width: 100em) {
    /*
     * .position-absolute\@xxl-only
     * .position-fixed\@xxl-only
     * .position-initial\@xxl-only
     * .position-inherit\@xxl-only
     * .position-relative\@xxl-only
     * .position-static\@xxl-only
     * .fixed-top\@xxl-only
     * .fixed-bottom\@xxl-only
     */
}
```

#### <a name="position-position"></a>`position()`

Helper `position` entry point.  
Combine both [`position-helper`](#position-helper) and [`position-helper-with-bp`](#position-helper-with-bp) helpers in one helper.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.position;
```

##### Parameters
| Type | Description | Mandatory | Default |
|---|---|---|---|
| `Boolean` | Use `position-helper-with-bp()` | `false` | `true` |

##### Output
See [`position-helper()`](#position-helper) and [`position-helper-with-bp()`](#position-helper-with-bp) outputs.

<br />
<br />

## stretched-link

- [Variables](#stretched-link-variables)
  - [`$zindex-stretched`](#stretched-link-variables-zindex-stretched)
- [Mixins](#stretched-link-mixins)
  - [`stretched-link-helper()`](#stretched-link-helper)
  - [`stretched-link-helper-with-bp()`](#stretched-link-helper-with-bp)
  - [`stretched-link()`](#stretched-link-stretched-link)

<br />

### <a name="stretched-link-variables"></a>Variables

This variable could be customized depending on what you need in your `variables.scss` file.  
Here is the default value.

#### <a name="stretched-link-variables-zindex-stretched"></a>`$zindex-stretched`
Define the z-index value for the link.

```scss
$zindex-stretched: 1 !default;
```

<br />

### <a name="stretched-link-mixins"></a>Mixins

#### <a name="stretched-link-helper"></a>`stretched-link-helper()`

Set stretched-link class.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.stretched-link-helper;
```

##### Output
```css
.stretched-link::after {
    bottom: 0;
    content: "";
    left: 0;
    pointer-events: auto;
    position: absolute;
    right: 0;
    top: 0;
    z-index: 1;
}
```

#### <a name="stretched-link-helper-with-bp"></a>`stretched-link-helper-with-bp()`

Set stretched-link class with breakpoints media queries.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.stretched-link-helper-with-bp;
```

##### Output
```css
@media (min-width: 20.375em) and (max-width: 35.99875em) {
    .stretched-link\@xs-only::after {
        bottom: 0;
        content: "";
        left: 0;
        pointer-events: auto;
        position: absolute;
        right: 0;
        top: 0;
        z-index: 1;
    }
}
/* and so on */
@media (min-width: 36em) {
    /*
     * .stretched-link\@sm
     */
}
@media (min-width: 36em) and (max-width: 47.99875em) {
    /*
     * .stretched-link\@sm-only
     */
}
@media (min-width: 48em) {
    /*
     * .stretched-link\@md
     */
}
@media (min-width: 48em) and (max-width: 63.99875em) {
    /*
     * .stretched-link\@md-only
     */
}
@media (min-width: 64em) {
    /*
     * .stretched-link\@lg
     */
}
@media (min-width: 64em) and (max-width: 74.99875em) {
    /*
     * .stretched-link\@lg-only
     */
}
@media (min-width: 75em) {
    /*
     * .stretched-link\@xl
     */
}
@media (min-width: 75em) and (max-width: 99.99875em) {
    /*
     * .stretched-link\@xl-only
     */
}
@media (min-width: 100em) {
    /*
     * .stretched-link\@xxl
     */
}
@media (min-width: 100em) {
    /*
     * .stretched-link\@xxl-only
     */
}
```

#### <a name="stretched-link-stretched-link"></a>`stretched-link()`

Helper `stretched-link` entry point.  
Combine both [`stretched-link-helper`](#stretched-link-helper) and [`stretched-link-helper-with-bp`](#stretched-link-helper-with-bp) helpers in one helper.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.stretched-link;
// @include helpers.stretched-link(false);
```

##### Parameters
| Type | Description | Mandatory | Default |
|---|---|---|---|
| `Boolean` | Use of `stretched-link-helper-with-bp()` | `false` | `true` |


##### Output
See [`stretched-link-helper()`](#stretched-link-helper) and [`stretched-link-helper-with-bp()`](#stretched-link-helper-with-bp) outputs.

<br />
<br />

## text

- [Variables](#text-variables)
  - [`$text-aligns`](#text-variables-text-aligns)
  - [`$text-transforms`](#text-variables-text-transforms)
  - [`$text-important`](#text-variables-text-important)
- [Mixins](#text-mixins)
  - [`text-aligns-helper()`](#text-aligns-helper)
  - [`text-transforms-helper()`](#text-transforms-helper)
  - [`text-miscs-helper()`](#text-miscs-helper)
  - [`text-helper-with-bp()`](#text-helper-with-bp)
  - [`text()`](#text-text)

<br />

### <a name="text-variables"></a>Variables

All those variables could be customized depending on what you need in your `variables.scss` file.  
Here are the default values.

#### <a name="text-variables-text-aligns"></a>`$text-aligns`
Define all text align values to support.

```scss
$text-aligns: (
    center,
    justify,
    left,
    right
) !default;
```

#### <a name="text-variables-text-transforms"></a>`$text-transforms`
Define all text transform values to support.

```scss
$text-transforms: (
    capitalize,
    lowercase,
    uppercase
) !default;
```

#### <a name="text-variables-text-important"></a>`$text-important`
Set the important property on each rules.

```scss
$text-important: true;
```

<br />

### <a name="text-mixins"></a>Mixins

#### <a name="text-aligns-helper"></a>`text-aligns-helper()`

Set all text-align classes from the [`$text-aligns`](#text-variables-text-aligns) variable.

```scss
@use '@wide/styles-helpers' as helpers;

/*
 * $text-aligns variable defined in `variables.scss`
 */
$text-aligns: (
    center,
    justify,
    left,
    right
) !default;
/* */

@include helpers.text-aligns-helper;
```

##### Output
```css
.text-center {
    text-align: center !important;
}

.text-justify {
    text-align: justify !important;
}

.text-left {
    text-align: left !important;
}

.text-right {
    text-align: right !important;
}
```

#### <a name="text-transforms-helper"></a>`text-transforms-helper()`

Set all text-transform classes from the [`$text-transforms`](#text-variables-text-transforms) variable.

```scss
@use '@wide/styles-helpers' as helpers;

/*
 * $text-transforms variable defined in `variables.scss`
 */
$text-transforms: (
    capitalize,
    lowercase,
    uppercase
) !default;
/* */

@include helpers.text-transforms-helper;
```

##### Output
```css
.text-capitalize {
    text-transform: capitalize !important;
}

.text-lowercase {
    text-transform: lowercase !important;
}

.text-uppercase {
    text-transform: uppercase !important;
}
```

#### <a name="text-miscs-helper"></a>`text-miscs-helper()`

Set text-miscs classes.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.text-miscs-helper;
```

##### Output
```css
.text-decoration-none {
    text-decoration: none !important;
}
.text-break {
    overflow-wrap: break-word !important;
    word-break: break-word !important;
}
.text-truncate {
    max-width: 100%;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
}
.text-wrap {
    white-space: normal !important;
}
.text-nowrap {
    white-space: nowrap !important;
}
.text-reset {
    color: inherit !important;
}
```

#### <a name="text-helper-with-bp"></a>`text-helper-with-bp()`

Combine [`text-aligns-helper`](#text-aligns-helper), [`text-transforms-helper`](#text-transforms-helper) and [`text-miscs-helper`](#text-miscs-helper) helpers in one helper with breakpoints media queries.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.text-helper-with-bp;
```

##### Output
```css
@media (min-width: 20.375em) and (max-width: 35.99875em) {
    .text-center\@xs-only {
        text-align: center !important;
    }

    .text-justify\@xs-only {
        text-align: justify !important;
    }

    .text-left\@xs-only {
        text-align: left !important;
    }

    .text-right\@xs-only {
        text-align: right !important;
    }

    .text-capitalize\@xs-only {
        text-transform: capitalize !important;
    }

    .text-lowercase\@xs-only {
        text-transform: lowercase !important;
    }

    .text-uppercase\@xs-only {
        text-transform: uppercase !important;
    }

    .text-decoration-none\@xs-only {
        text-decoration: none !important;
    }
    .text-break\@xs-only {
        overflow-wrap: break-word !important;
        word-break: break-word !important;
    }
    .text-truncate\@xs-only {
        max-width: 100%;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
    }
    .text-wrap\@xs-only {
        white-space: normal !important;
    }
    .text-nowrap\@xs-only {
        white-space: nowrap !important;
    }
    .text-reset\@xs-only {
        color: inherit !important;
    }
}
/* and so on */
@media (min-width: 36em) {
    /*
     * .text-center\@sm
     * .text-justify\@sm
     * .text-left\@sm
     * .text-right\@sm
     * .text-capitalize\@sm
     * .text-lowercase\@sm
     * .text-uppercase\@sm
     * .text-decoration-none\@sm
     * .text-break\@sm
     * .text-truncate\@sm
     * .text-wrap\@sm
     * .text-nowrap\@sm
     * .text-reset\@sm
     */
}
@media (min-width: 36em) and (max-width: 47.99875em) {
    /*
     * .text-center\@sm-only
     * .text-justify\@sm-only
     * .text-left\@sm-only
     * .text-lerightft\@sm-only
     * .text-capitalize\@sm-only
     * .text-lowercase\@sm-only
     * .text-uppercase\@sm-only
     * .text-decoration-none\@sm-only
     * .text-break\@sm-only
     * .text-truncate\@sm-only
     * .text-wrap\@sm-only
     * .text-nowrap\@sm-only
     * .text-reset\@sm-only
     */
}
@media (min-width: 48em) {
    /*
     * .text-center\@md
     * .text-justify\@md
     * .text-left\@md
     * .text-right\@md
     * .text-capitalize\@md
     * .text-lowercase\@md
     * .text-uppercase\@md
     * .text-decoration-none\@md
     * .text-break\@md
     * .text-truncate\@md
     * .text-wrap\@md
     * .text-nowrap\@md
     * .text-reset\@md
     */
}
@media (min-width: 48em) and (max-width: 63.99875em) {
    /*
     * .text-center\@md-only
     * .text-justify\@md-only
     * .text-left\@md-only
     * .text-right\@md-only
     * .text-capitalize\@md-only
     * .text-lowercase\@md-only
     * .text-uppercase\@md-only
     * .text-decoration-none\@md-only
     * .text-break\@md-only
     * .text-truncate\@md-only
     * .text-wrap\@md-only
     * .text-nowrap\@md-only
     * .text-reset\@md-only
     */
}
@media (min-width: 64em) {
    /*
     * .text-center\@lg
     * .text-justify\@lg
     * .text-left\@lg
     * .text-right\@lg
     * .text-capitalize\@lg
     * .text-lowercase\@lg
     * .text-uppercase\@lg
     * .text-decoration-none\@lg
     * .text-break\@lg
     * .text-truncate\@lg
     * .text-wrap\@lg
     * .text-nowrap\@lg
     * .text-reset\@lg
     */
}
@media (min-width: 64em) and (max-width: 74.99875em) {
    /*
     * .text-center\@lg-only
     * .text-justify\@lg-only
     * .text-left\@lg-only
     * .text-right\@lg-only
     * .text-capitalize\@lg-only
     * .text-lowercase\@lg-only
     * .text-uppercase\@lg-only
     * .text-decoration-none\@lg-only
     * .text-break\@lg-only
     * .text-truncate\@lg-only
     * .text-wrap\@lg-only
     * .text-nowrap\@lg-only
     * .text-reset\@lg-only
     */
}
@media (min-width: 75em) {
    /*
     * .text-center\@xl
     * .text-justify\@xl
     * .text-left\@xl
     * .text-right\@xl
     * .text-capitalize\@xl
     * .text-lowercase\@xl
     * .text-uppercase\@xl
     * .text-decoration-none\@xl
     * .text-break\@xl
     * .text-truncate\@xl
     * .text-wrap\@xl
     * .text-nowrap\@xl
     * .text-reset\@xl
     */
}
@media (min-width: 75em) and (max-width: 99.99875em) {
    /*
     * .text-center\@xl-only
     * .text-justify\@xl-only
     * .text-left\@xl-only
     * .text-right\@xl-only
     * .text-capitalize\@xl-only
     * .text-lowercase\@xl-only
     * .text-uppercase\@xl-only
     * .text-decoration-none\@xl-only
     * .text-break\@xl-only
     * .text-truncate\@xl-only
     * .text-wrap\@xl-only
     * .text-nowrap\@xl-only
     * .text-reset\@xl-only
     */
}
@media (min-width: 100em) {
    /*
     * .text-center\@xxl
     * .text-justify\@xxl
     * .text-left\@xxl
     * .text-right\@xxl
     * .text-capitalize\@xxl
     * .text-lowercase\@xxl
     * .text-uppercase\@xxl
     * .text-decoration-none\@xxl
     * .text-break\@xxl
     * .text-truncate\@xxl
     * .text-wrap\@xxl
     * .text-nowrap\@xxl
     * .text-reset\@xxl
     */
}
@media (min-width: 100em) {
    /*
     * .text-center\@xxl-only
     * .text-justify\@xxl-only
     * .text-left\@xxl-only
     * .text-right\@xxl-only
     * .text-capitalize\@xxl-only
     * .text-lowercase\@xxl-only
     * .text-uppercase\@xxl-only
     * .text-decoration-none\@xxl-only
     * .text-break\@xxl-only
     * .text-truncate\@xxl-only
     * .text-wrap\@xxl-only
     * .text-nowrap\@xxl-only
     * .text-reset\@xxl-only
     */
}
```

#### <a name="text-text"></a>`text()`

Helper `text` entry point.   
Combine [`text-aligns-helper`](#text-aligns-helper), [`text-transforms-helper`](#text-transforms-helper), [`text-miscs-helper`](#text-miscs-helper) and [`text-helper-with-bp`](#text-helper-with-bp) helpers in one helper.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.text;
// @include helpers.text(false);
```

##### Output
See [`text-aligns-helper()`](#text-aligns-helper), [`text-transforms-helper()`](#text-transforms-helper), [`text-miscs-helper()`](#text-miscs-helper) and [`text-helper-with-bp()`](#text-helper-with-bp) outputs.

<br />
<br />

## visibility

- [Variables](#visibility-variables)
  - [`$visibilities`](#visibility-variables-visibilities)
  - [`$visibilities-important`](#visibility-variables-visibilities-important)
  - [`$visibilities-prefix`](#visibility-variables-visibilities-prefix)
- [Mixins](#visibility-mixins)
  - [`visibility-helper()`](#visibility-helper)
  - [`visibility-helper-with-bp()`](#visibility-helper-with-bp)
  - [`visibility-print-helper()`](#visibility-print-helper)
  - [`visibility-screen-helper()`](#visibility-screen-helper)
  - [`visibility()`](#visibility-visibility)

<br />

### <a name="visibility-variables"></a>Variables

All those variables could be customized depending on what you need in your `variables.scss` file.  
Here are the default values.

#### <a name="visibility-variables-visibilities"></a>`$visibilities`
Define all visibility values to support.

```scss
$visibilities: (
    visible,
    hidden
) !default;
```

#### <a name="visibility-variables-visibilities-important"></a>`$visibilities-important`
Set the important property on each rules.

```scss
$visibilities-important: true;
```

#### <a name="visibility-variables-visibilities-prefix"></a>`$visibilities-prefix`
Define the prefix of all visibility classes.

```scss
$visibilities-prefix: 'v-';
```

<br />

### <a name="visibility-mixins"></a>Mixins

#### <a name="visibility-helper"></a>`visibility-helper()`

Set all visibility classes from the [`$visibilities`](#visibility-variables-visibilities) variable.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.visibility-helper;
```

##### Output
```css
.v-visible {
    visibility: visible !important;
}

.v-hidden {
    visibility: hidden !important;
}
```

#### <a name="visibility-helper-with-bp"></a>`visibility-helper-with-bp()`

Set all visibility classes from the [`$visibilities`](#visibility-variables-visibilities) variable with breakpoints media queries.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.visibility-helper-with-bp;
```

##### Output
```css
@media (min-width: 20.375em) and (max-width: 35.99875em) {
    .v-visible\@xs-only {
        visibility: visible !important;
    }

    .v-hidden\@xs-only {
        visibility: hidden !important;
    }
}
/* and so on */
@media (min-width: 36em) {
    /*
     * .v-visible\@sm
     * .v-hidden\@sm
     */
}
@media (min-width: 36em) and (max-width: 47.99875em) {
    /*
     * .v-visible\@sm-only
     * .v-hidden\@sm-only
     */
}
@media (min-width: 48em) {
    /*
     * .v-visible\@md
     * .v-hidden\@md
     */
}
@media (min-width: 48em) and (max-width: 63.99875em) {
    /*
     * .v-visible\@md-only
     * .v-hidden\@md-only
     */
}
@media (min-width: 64em) {
    /*
     * .v-visible\@lg
     * .v-hidden\@lg
     */
}
@media (min-width: 64em) and (max-width: 74.99875em) {
    /*
     * .v-visible\@lg-only
     * .v-hidden\@lg-only
     */
}
@media (min-width: 75em) {
    /*
     * .v-visible\@xl
     * .v-hidden\@xl
     */
}
@media (min-width: 75em) and (max-width: 99.99875em) {
    /*
     * .v-visible\@xl-only
     * .v-hidden\@xl-only
     */
}
@media (min-width: 100em) {
    /*
     * .v-visible\@xxl
     * .v-hidden\@xxl
     */
}
@media (min-width: 100em) {
    /*
     * .v-visible\@xxl-only
     * .v-hidden\@xxl-only
     */
}
```

#### <a name="visibility-print-helper"></a>`visibility-print-helper()`

Set all visibility classes from the [`$visibilities`](#visibility-variables-visibilities) variable in print media query.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.visibility-print-helper;
```

##### Output
```css
@media print {
    /*
     * .v-visible
     * .v-hidden
     */
}
```

#### <a name="visibility-screen-helper"></a>`visibility-screen-helper()`

Set all visibility classes from the [`$visibilities`](#visibility-variables-visibilities) variable in screen media query.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.visibility-screen-helper;
```

##### Output
```css
@media screen {
    /*
     * .v-visible
     * .v-hidden
     */
}
```

#### <a name="visibility-visibility"></a>`visibility()`

Helper `visibility` entry point.  
Combine both [`visibility-helper`](#visibility-helper) and [`visibility-helper-with-bp`](#visibility-helper-with-bp) helpers in one helper.

```scss
@use '@wide/styles-helpers' as helpers;

@include helpers.visibility;
// @include helpers.visibility(false);
```

##### Parameters
| Type | Description | Mandatory | Default |
|---|---|---|---|
| `Boolean` | Use `visibility-helper-with-bp()` | `false` | `true` |

##### Output
See [`visibility-helper`](#visibility-helper) and [`visibility-helper-with-bp`](#visibility-helper-with-bp) outputs.

<br />
<br />

## Authors

- **Aymeric Assier** - [github.com/myeti](https://github.com/myeti)
- **Julien Martins Da Costa** - [github.com/jdacosta](https://github.com/jdacosta)

<br />

### Contributors

- **Sébastien Robillard** - [github.com/robiseb](https://github.com/robiseb)

<br />
<br />

## Resources 
- [Locomotive boilerplate](https://github.com/locomotivemtl/locomotive-boilerplate)

<br />
<br />

## License

This project is licensed under the MIT License - see the [licence](licence) file for details