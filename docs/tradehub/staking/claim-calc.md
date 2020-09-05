## Interactive Dashboard

> Special thanks to Kang, Intsol, Vincent, and Guardians for their work on this!

https://public.tableau.com/profile/kang.long#!/vizhome/SWTHStakingAnalysis/ReadMe

## Interest Rate Calculation

> The origin of this discussion was from Telegram and thought it was worth including in this guide to help others have an idea around how often one should claim and stake.

The dashboard above also takes into consideration the bonded percent of tokens, which significantly impacts the amount of rewards available while the formula below does not take the bonding percentage into consideration.

## Variables

`a` -> Principal in Switcheo (SWTH)

`x` -> Claiming frequency per year

`c` -> Fees Required (ex. 2 for claim, 1 for stake = 3)

`i` -> Estimated APR for the year

## Equation

![formula](https://latex.codecogs.com/svg.latex?\Huge&space;\color{Pink}&space;f(x)=a(1+\frac{i}{x})^x-(cx))
<!-- <img src="https://latex.codecogs.com/svg.latex?\Huge&space;\color{Pink}&space;f(x)=a(\frac{1 + i}{x})^x - (cx)" title="\Large \color{Pink} x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}" /> -->

## Example #1 - Claim once a week

`a` -> 100,000 SWTH

`x` -> 1 time per week; 52

`c` -> 3

`i` -> 110% (1.1)

![formula](https://latex.codecogs.com/svg.latex?\Huge&space;\color{Pink}&space;f(x)=100,000(1+\frac{1.1}{52})^{52}-(3*52))

![formula](https://latex.codecogs.com/svg.latex?\Huge&space;\color{Pink}&space;f(x)=296,834)


## Example #2 - Claim once a day

`a` -> 100,000 SWTH

`x` -> 1 time per day; 365

`c` -> 3

`i` -> 110% (1.1)

![formula](https://latex.codecogs.com/svg.latex?\Huge&space;\color{Pink}&space;f(x)=100,000(1+\frac{1.1}{365})^{365}-(3*365))

![formula](https://latex.codecogs.com/svg.latex?\Huge&space;\color{Pink}&space;f(x)=298,825)

## Optimizing this formula

This formula is an estimation but does a good job of helping you understand how different variables effect the outcome of the amount of Switcheo you will end up with at the end of the year.

This formula has an optimal `x` value of 388 times, meaning slightly more than once a day over the course of a year.

![formula](https://latex.codecogs.com/svg.latex?\Huge&space;\color{Pink}&space;x'=388)

Even if you don't hit this number but instead opt for slighly lower time intervals (weekly) you are still getting very close to optimal rewards.