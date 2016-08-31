# How to avoid arithmetic overflow in certain cases?

If there's an expression in the form of -
   A / B

* where calculating A and/or B will result into arithmetic overflow but the result of A/B is within the range

First, a few logarithmic rules that we are going to use. Assuming b is the base -

   x = b ^ log x
   log (x*y) = log x - log y
   log (x/y) = log x - logy
   log (x^y) = y * log x

Applying them -

   A / B = e ^ log (A/B)
   log (A/B) = log A - log B

log A or log B is a much smaller value than A or B themselves.

If A = a0 * a1 * a2 * ... * an, log A = log a0 + log a1 + log a2 + ... + logn. The same goes true for B.

If A = a0 + a1 + a2 + ... + an and B is either B = b0 * b1 * b2 * ... * bm or some number within the range, then

   A / B = a0 / b0 * b1 * b2 * ... * bm + a1 / b0 * b1 * b2 * ... * bm + ... + an / b0 * b1 * b2 * ... * bm
   a0 / b0 * b1 * b2 * ... * bm = e ^ log (a0/(b0*b1*b2* ... *bm))
   log (a0/(b0*b1*b2* ... *bm)) = log a0 - log b0 - log b1 - ... - log bm