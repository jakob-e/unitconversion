_unitconversion.scss
==============

**CONVERT ANYTHING (ALMOST)**

At the moment the following units are supported (to the best extend possible – please comment):

````SCSS
px, pt, pc, in, mm, cm, em, rem, ex, ch, vw, vh, vmin, vmax, 
deg, rad, grad, turn, dpi, dpcm, dppx, s, ms, hz, khz, number
````


**SIMPLE SYNTAX**

Rather than going with the "good" old fromUnit-to-toUnit(fromUnit) syntax this function set is based on toUnit(fromUnit) making it a lot shorter and less cumbersome to maintain – as shown below :-)

````SCSS
       pt-to-px(input);
       pc-to-px(input);       
       in-to-px(input);       
       mm-to-px(input);    ==>   px(input);   
       cm-to-px(input);              
       em-to-px(input);              
       rem-to-px(input);                     
       num-to-px(input);  
`````
**NOTE!**

* To allow conversion between relative and absolute lengths em and rem are calculated as pixel values based on base-font-size (16px browser default). If you change the base font size of your document – remember to set the $base-font-size variable accordingly.

* To ease the job of handling compounds the em function takes multiple arguments. Each argument is treated as an em compound and used to calculate the visual size.
Example – how to set a visual size of 18px on a class nested in an element with a font-size of 2em:
````SCSS
      .class {
          font-size: em(18px, 2em);  ==>   0.5625em;
      }
`````
* If you use unit conversion in relation to the font shorthand syntax be aware that line-height "/" will cause division. To prevent this from happening you can either either interpolate the value or use + to add the pieces together without calculation:
````SCSS
      h2 { 
          font:300 em(24px)+/3 'Lato', sans-serif;
      }
      //  or
      h2 { 
          font:300 #{em(24px)}/3 'Lato', sans-serif;
      }
````
* At the moment LibSass does not support native conversion of the following units: dpi, dpcm, dppx, s, ms, Hz and kHz . Also note that you must run the latest version (3.1 I think) supporting angles... but chances are you'll be 95% fine.
* $cast-string-to-unit: true; allows you to cast a string to a unit. This feature is highly experimental and in the category of Chris-Eppstein-would-never-do-that. Does not work in LibSass – use at own risk!
````SCSS
      .class {
        width: px("20em") + px(4);  ==>  324px;
      }
    
````
````SCSS
// ____________________________________________________________________________
//
//    Unit Conversion v.2.0
// ____________________________________________________________________________
//
//   Function               Input units    
//     
//   Absolute length      
//   px(input);             px, pt, pc, in, mm, cm, em, rem, number
//   pt(input);             px, pt, pc, in, mm, cm, em, rem, number
//   pc(input);             px, pt, pc, in, mm, cm, em, rem, number
//   in(input);             px, pt, pc, in, mm, cm, em, rem, number
//   mm(input);             px, pt, pc, in, mm, cm, em, rem, number
//   cm(input);             px, pt, pc, in, mm, cm, em, rem, number
//
//   Relative length 
//   em(input);             px, pt, pc, in, mm, cm, em, rem, number
//   rem(input);            px, pt, pc, in, mm, cm, em, rem, number
//   ex(input);             ex, number  
//   ch(input);             ch, number
//   vw(input);             vw, number
//   vh(input);             vh, number
//   vmin(input);           vmin, number  
//   vmax(input);           vmax, number
//
//   Angle
//   deg(input);            deg, rad, grad, turn, number
//   rad(input);            deg, rad, grad, turn, number
//   grad(input);           deg, rad, grad, turn, number
//   turn(input);           deg, rad, grad, turn, number
//
//   Resolution
//   dpi(input);            dpi, dpcm, dppx, number
//   dpcm(input);           dpi, dpcm, dppx, number
//   dppx(input);           dpi, dpcm, dppx, number
//
//   Time
//   s(input);              s, ms, number
//   ms(input);             s, ms, number
//
//   Frequency
//   hz(input);             hz, khz, number
//   khz(input);            hz, khz, number
//  
//   String
//   str(input);            anything not null
//
//   Number, int and uint
//   num(input);            px, pt, pc, in, mm, cm, em, rem, ex, ch,
//                          vw, vh, vmin, vmax, deg, rad, grad, turn,
//                          dpi, dpcm, dppx, s, ms, hz, khz, number
//   int(input);            as number
//   uint(input);           as number
//
//   Aliases
//   string(input);
//   number(input);
//
// ____________________________________________________________________________
````

Please comment :)
