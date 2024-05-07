# SynastriaCoreLib

A collection of common functions needed by other addons

## Installation

1. Download the [latest release](https://github.com/imevul/SynastriaCoreLib/releases)
2. Extract to Interface/AddOns and enable the addon in-game

## Embedding

You can embed SynastriaCoreLib in your own addon. Make sure you include all required libraries (from the `/Libs` folder), and then put the `SynastriaCoreLib-1.0` folder in there as well, as a library.
You are then able to include it in your `embed.xml` or `.toc` file:

`<Include file="Libs\SynastriaCoreLib-1.0\SynastriaCoreLib-1.0.xml" />`
