# Paths, paths and more kind of paths

Source - http://www.vlsi-expert.com/2011/03/static-timing-analysis-sta-basic-timing.html

## Timing paths considered during timing analysis

1. Data path
2. Clock path
3. Clock gating path
4. Asynchronous path

## Data path
1. Input pin to output pin (combinational logic in between)
2. Register to register which is clock input of one register to the data input of the next flop. There may be combinational logic in between the two registers.
3. Input pin to register data pin
4, Register to output port which is register clock pin to output port

## Clock path

Clock input port of the design to the clock input of each register.

## Clock gating path

Basically a gated clock path

## Asynchronous path

I don't understand this shit! :confused:

## Other types of paths

Oh yeah -

### False path

Paths that should not be considered during timing analysis. For example paths emerging from pins of the design that are tied to VCC or GND, or pins for testing purpose. The STA tools  should be told to ignore them so that they don't try to be oversmart and analyze these paths and make changes in the design to resolve if thee are any violations on these paths.

### Critical path

Path of longest delay. Delay is between clock input of one flop to the data input of the next flop.

### Multicycle path

Path where data is allowed to take more than one cycle to propagate from the start point to the endpoint

### Single cycle path

Meh

### Launch clock path and Capture clock path

Consider a flop to flop path.
Launch flop = start flop, launches the data
Capture flop = end flop, captures the data

Launch clock path = clock path responsible for launching the data
Capture clock path = clock path responsible for capturing the data