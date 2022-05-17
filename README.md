# AssemblyLanguage
these are the registers that will be used during this program
split:
X5 holds the original float in binary
X7 holds the mask for the sign (32768)
X1 holds the sign (5+7)

X7 now holds mask for exponent
X2 holds exponent (5+ changed 7)
X2 is then just shifted to account

X7 now holds mask for fraction
X3 is the AND version to account for (5 , 7)
moxing X7 over to hold mask for mantissa
X2 and X3 then get put into the stack pointer SP
(repeat same registers for usage with second number)

add:
X2 holds the loaded mantissa from SP 
X22 holds the multiplied mantissa's
X1 holds the loaded SP #0
X16 holds loaded SP #8
X17 holds loaded SP # 32
X2 now holds the added exponents from the SP
X5 holds the final and stored back into SP at #56

combine:
X2 holds the biased exponent
X2 now is shifted 10 bits to the left for proper position
X7 mask for fraction
X3 is stripped from the leading bits
X5 holds the combined exponent with fraction

normalize:
X7 holds mask for mantissa
then returned

main:
X1 stores num1
X2 stores num2
H1 changes type of X1
H2 changes type of X2
X9 holds the adress of num1
W9 loads X9 into W1 (lower 16 bits)
X10 holds address of num2
W2 same as W9 (loading)
X11 fadd's
X12 is delcaring lo12:fmul
H4 holds h1*h2
H4 then stored into [X12]
X13, X14 now loading back into the stack pointer in #48 and #56

