# Audio Source Selector

## Overview
This plugin is a wrapper for the built-in Router component that provides drop-down menus for the source selection. All audio routing is done by the Router. All source selection done in the plugin is passed to the Router and all feedback from the router is passed back to the plugin.

## License
```
Copyright (C) 2024 Jonathan Dean (ke4ukz@gmx.com)

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Lesser General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Lesser General Public License for more details.

You should have received a copy of the GNU Lesser General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.
```

## Usage
Copy the `Audio Source Selector.qplug` file to `%USERPROFILE%\Documents\QSC\Q-Sys Designer\Plugins\`. Q-SYS Designer will load the plugin automatically.

## Run Time Properties

### Labels
These text fields control the text in the source selection drop-down controls on the [`Selectors`](#selectors) tab. Input and output pins are provided for each.

### Selectors
Each drop-down control selects the input that will be routed to each output, and also shows the name of the currently-selected input for each. Input pins accept text values, but for routing to work the text must match the input name exactly.

### Knobs
These knobs provide a way to route inputs to outputs numerically. Only one output and input may be selected at a time. See [Numeric Routing Logic](#numeric-routing-logic) for details on how this works.

### Buttons
These buttons provide matrix-mixer-like routing. Each output may have only one input selected. The buttons show which input is currently selected. (There is a bug where the buttons do not show the feedback until routing has been performed once, but after that the feedback is correct.)

## Design Time Properties
Property			| Function
--------------------|-------------------
`Debug Print`		| Specify what debug messages to print (All, Function Calls, or None)
`Inputs`			| Number of inputs (8, 16, 32, or 64)
`Outputs`			| Number of outputs (8, 16, 32, or 64)
`Numeric Routing`	| See [Numeric Routing Logic](#numeric-routing-logic)
`Show Debug`		| Show debug window in component controls window

## Numeric Routing Logic
Value						| Meaning
----------------------------|------------------
`Route on input change`		| When the `Input Select` knob changes, routing is done for whichever output is already selected (select the output first, then select the input to use)
`Route on output change`	| When the `Output Select` knob changes, routing is done for whichever input is selected (select your input first, then select the output)
`Route on either change`	| When either the `Input Select` or the `Output Select` knobs are changed, the routing is done for whatever value the other currently has (this is kind of weird, but who knows someone may want it)
`Route on trigger only`		| Set the selected `Output Select` input to `Input Select` only when the `Execute Route` button is triggered
