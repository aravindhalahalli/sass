//Genearting custom utility classes
$font-sizes: (
  xxl: 21px,
  xl:  18px,
  l:   16px,
  m:   14px,
  s:   12px,
  xs:  10px
);

$font-list: xxl xl l m s xs;

@each $size in $font-list {
  .font-#{$size} {
    font-size: map-get($font-sizes, $size) !important;
  }
}
//Shashank method need to work on it for font-size

$messagecolor: red;
$bgcolor: powderblue;
$breakpoints: (
  554px,
  768px,
  991px
);

$font:(
    12px,
    24px,
    32px
);

@mixin font-size-prep {
  @for $i from 1 through $breakpoints {
    @media only screen and (max-width: 767px){
        @for $i from 1 through $breakpoints{
            .font-#{$i}-m { @extend %float-styles; }
        }
    }
    @media only screen and (min-width: 767px){

    }
    @media only screen and (min-width: 991px){

    }
    @media only screen and (min-width: 1200px){

    }
  }
}

@include  font-size-prep;

//


jsdfksghgks
//Custom Utility classes for margin, paddding with only responsive.
$sides: (
"": "",
"t": "top",
"b": "bottom",
"l": "left",
"r": "right",
);

$breakpoints: (
"": "",
"xs": 576px,
"sm": 768px,
"md": 992px,
"lg": 1200px,
);
$size: 18px, 24px, 32px, 42px;
// margin 18,24,48,32

@each $breakName, $breakValue in $breakpoints {
  @each $sideName, $sideValue in $sides {
    @for $i from 0 through length($size) {
      
      $property: if($sideName == '', '', -#{$sideValue});
      $space: $i * 1;
      $selector: '';

      @if $breakName != "" {
        $selector: #{$sideName}-#{$breakName}-#{$i[]};
      } @else {
        $selector: #{$sideName}-#{$i[]};
      }

      @if $breakName != "" {
        @media (min-width: $breakValue) {
          .m#{$selector} {
            margin#{$property}: #{$space}px;
          }
  
          .p#{$selector} {
            padding#{$property}: #{$space}px;
          }
        }
      } @else {
        .m#{$selector} {
          margin#{$property}: #{$space}px;
        }

        .p#{$selector} {
          padding#{$property}: #{$space}px;
        }
      }
    }
  }
}


//Generating custom class for text-alignment.
@mixin generate-responsive() {
    // Create a list of sizes and widths
    $sizes: (
      sm: "480px",
      md: "600px",
      lg: "800px"
    );
  
    // Base style, without a suffix
    @content;
  
    // Responsive styles
    // Loop over each size
    @each $suffix, $width in $sizes {
      @media (min-width: $width) {
        &-#{$suffix} { @content; }
      }
    }
  }
  
  .text-left {
    @include generate-responsive() {
      text-align: left;
    }
  }
  .text-center {
    @include generate-responsive() {
      text-align: center;
    }
  }
  .text-right {
    @include generate-responsive() {
      text-align: right;
    }
  }

//Generating font-size.
// $sizes: 160;

// @mixin font-classes{
// @for $i from 1 through $sizes {
//     .font-#{$i} {
//       font-size: #{$i}px;
//     }
//   }
// }
// @include font-classes;

$fnt-size: 12px,16px,18px,24px,32px,48px;

@each $current-fnt in $fnt-size {
    $i: index($fnt-size, $current-fnt);
    .fontsize-#{$current-fnt} { 
        font-size: $current-fnt;
    }
}

$sizes: 160;
//Generating classes for margin and padding.
@mixin margin-classes {
  @for $i from 1 through $sizes {
     $margin: $i * 0.25rem;
    /* margin #{$margin} */
    .m#{$i}  {margin: $margin;}
    .ml#{$i} {margin-left: $margin;}
    .mr#{$i} {margin-right: $margin;}
    .mt#{$i} {margin-top: $margin;}
    .mb#{$i} {margin-bottom: $margin;}
    .mx#{$i} {margin-left: $margin; margin-right: $margin;}
    .my#{$i} {margin-top: $margin; margin-bottom: $margin;}
  }
}
@include margin-classes;


@mixin padding-classes {
  @for $i from 1 through $sizes {
    $padding: $i * 0.25rem;
    /* padding #{$padding} */
    .p#{$i} {padding: $padding;}
    .pl#{$i} {padding-left: $padding;}
    .pr#{$i} {padding-right: $padding;}
    .pt#{$i} {padding-top: $padding;}
    .pb#{$i} {padding-bottom: $padding;}
    .px#{$i} {padding-left: $padding; padding-right: $padding;}
    .py#{$i} {padding-top: $padding; padding-bottom: $padding;}
  }
}
@include padding-classes;



//colors determination with color's
$styles: (
  error: (red, white, 1rem),
  success: (green, white, 1rem),
  warning: (yellow, black, 1rem)
);

.button {
  display: inline-block;
  background-color: lightgray;
  color: darkgray;
  padding: 0.5rem;
  
  @each $type, $style in $styles {
    $background-color: nth($style, 1);
    $font-color: nth($style, 2);
    $padding: nth($style, 3);

    &--#{$type} {
      background-color: $background-color;
      color: $font-color;
      padding: $padding;
    }
  }
}