_unitconversion.scss
==============

CONVERT ANYTHING (ALMOST)
At the moment the following units are supported (to the best extend possible – please comment):
````SCSS
px, pt, pc, in, mm, cm, em, rem, ex, ch, vw, vh, vmin, vmax, deg, rad, grad, turn, dpi, dpcm, dppx, s, ms, hz, khz, number
````


SIMPLE SYNTAX
Rather than going with the "good" old fromUnit-to-toUnit(fromUnit) syntax this function set is based on toUnit(fromUnit) making it a lot shorter and less cumbersome to maintain – as shown below :-)
````SCSS
    // ========================================================== 
    // Unit Conversion
    // ========================================================== 
    // 
    // Functions:
    // ----------------------------------------------------------  
    // 
    //  NUMBER:
    //    
    //  isNaN($value)  - returns true or false if type-of($value)==number
    // 
    //  number($value) - returns a unitless number.
    // 
    //  int($value)    - returns a unitless integer. 
    // 
    //  uint($value)   - returns a unitless unsigned integer. 
    //
    // 
    //  UNITS: 
    // 
    //  px($value)     - converts a number or unit to px.
    //                     
    //  em($args...)   - converts a number or unit to em. 
    // 
    //                    To adjust for em compounds you can add
    //                    aditional arguments to calculate the 
    //                    visual em size. em(visual-size,....)
    //                               
    //                    Example:  em(2, 2em, 2em) => 0.5em
    //
    //  rem($value)    - converts a number or unit to rem. 
    // 
    //  pt($value)     - converts a number or unit to pt. 
    // 
    //  pc($value)     - converts a number or unit to pc. 
    // 
    //  in($value)     - converts a number or unit to in. 
    // 
    //  cm($value)     - converts a number or unit to cm. 
    //
    // 
    // PERCENTAGE:
    // 
    //  pct($value,$base:100)   - similar to precentage, but takes a base
    //                            value (100%) to be used for calculating 
    //                            the precent value returned
    //                            
    //                            Example:  pct(1,100)     => 1%   
    //                                      pct(1,1)       => 100%
    //                                      pct(50,250)    => 20%
    //                                      pct(10px,16px) => 62.5%
    //                                      pct(1em,16px)  => 100%
    //   
    // ANGLE:
    // 
    //  deg($value)     - converts a number or angle unit to deg.  
    // 
    //  grad($value)    - converts a number or angle unit to grad.
    //
    //  turn($value)    - converts a number or angle unit to turn.
    //
    //  rad($value)     - converts a number or angle unit to rad.  
    // 
    // 
    // 
    //  CONVERT:
    // 
    //   Allows conversion by based on unit parameter
    // 
    //   $unit:px !default;
    //   convert($unit,2em)  - converts 2ems to pixels.  
    // 
    // ========================================================== 
    // Unit Conversion Table
    // http://www.translatorscafe.com/cafe/units-converter/typography/
    //      1px = 0.0625pc;
    //      1px = 0.75pt;  
    //      1px = 0.010416667in;    
    //      1px = 0.264583333mm;
    //      1px = 0.026458333cm;
    //
    // Angles
    // http://www.w3.org/TR/css3-values/#angles
    //      Full circle = 360deg = 400grad =  1turn = 2πrad
    //      1deg =  1.111111111grad  (400/360)
    //      1deg =  0.002777778turn  (1/360)
    //      1deg =  0.017453293rad   (180/π) 
    // 
    // ==========================================================
````

Please comment :)
