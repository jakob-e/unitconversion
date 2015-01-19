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
