_unitconversion.scss
==============

**Convert Anything** (almost)

At the moment the following units are supported (to the best extend possible – please comment):

````SCSS
px, pt, pc, in, mm, cm, em, rem, ex, ch, vw, vh, vmin, vmax, 
deg, rad, grad, turn, dpi, dpcm, dppx, s, ms, hz, khz, number
````


**Simple Syntax**

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
**Note!**

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
<table>
<tr><th colspan="3">Conversion table</th></tr>
<tr><td>Type</td><td>Function</td><td>Input units</td></tr>
<tr><td>Absolute length</td><td>px($input);</td><td>px, pt, pc, in, mm, cm, em, rem, number</td></tr>
<tr><td>               </td><td>pt($input);</td><td>px, pt, pc, in, mm, cm, em, rem, number</td></tr>
<tr><td>               </td><td>pc($input);</td><td>px, pt, pc, in, mm, cm, em, rem, number</td></tr>
<tr><td>               </td><td>in($input);</td><td>px, pt, pc, in, mm, cm, em, rem, number</td></tr>
<tr><td>               </td><td>mm($input);</td><td>px, pt, pc, in, mm, cm, em, rem, number</td></tr>
<tr><td>               </td><td>cm($input);</td><td>px, pt, pc, in, mm, cm, em, rem, number</td></tr>

<tr><td>Relative length</td><td>em($input);</td><td>px, pt, pc, in, mm, cm, em, rem, number</td></tr>
<tr><td>               </td><td>rem($input);</td><td>px, pt, pc, in, mm, cm, em, rem, number</td></tr>
<tr><td>               </td><td>ex($input);</td><td>ex, number                              </td></tr>
<tr><td>               </td><td>ch($input);</td><td>ch, number                              </td></tr>
<tr><td>               </td><td>vw($input);</td><td>vw, number                              </td></tr>
<tr><td>               </td><td>vh($input);</td><td>vh, number                              </td></tr>
<tr><td>               </td><td>vmin($input);</td><td>vmin, number                          </td></tr>
<tr><td>               </td><td>vmax($input);</td><td>vmax, number                          </td></tr>

<tr><td>Angle          </td><td>deg($input);</td><td>deg, rad, grad, turn, number           </td></tr>
<tr><td>               </td><td>rad($input);</td><td>deg, rad, grad, turn, number           </td></tr>
<tr><td>               </td><td>grad($input);</td><td>deg, rad, grad, turn, number          </td></tr>
<tr><td>               </td><td>turn($input);</td><td>deg, rad, grad, turn, number          </td></tr>

<tr><td>Resolution     </td><td>dpi($input);</td><td>dpi, dpcm, dppx, number                </td></tr>
<tr><td>               </td><td>dpcm($input);</td><td>dpi, dpcm, dppx, number               </td></tr>
<tr><td>               </td><td>dppx($input);</td><td>dpi, dpcm, dppx, number               </td></tr>

<tr><td>Time           </td><td>ms($input);</td><td>ms, s, number                           </td></tr>
<tr><td>               </td><td>s($input);</td><td> ms, s, number                            </td></tr>

<tr><td>Frequency      </td><td>hz($input);</td><td>Hz, kHz, number                         </td></tr>
<tr><td>               </td><td>khz($input);</td><td>Hz, kHz, number                        </td></tr>


<tr><td>String        </td><td>str($input);<br>string($input);</td><td>Anything not null                       </td></tr>
<tr><td>Number        </td><td>num(input);<br>number($input)</td>
<td>px, pt, pc, in, mm, cm, em, rem, ex, ch,<br>vw, vh, vmin, vmax, deg, rad, grad, turn,<br>dpi, dpcm, dppx, s, ms, hz, khz, number</td></tr>
<tr><td>              </td><td>int($input);</td><td align="center">″</td></tr>
<tr><td>              </td><td>uint($input);</td><td align="center">″</td></tr>
</table>


//  
//   String
//   str(input);            anything not null



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
