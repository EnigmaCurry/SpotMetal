SpotMetal
=========

This is an OpenOffice.org Calc extension to retrieve the current market value (spot price) of precious metals.

This should be a good example of a simple Calc extension for basing your own off of.

The extension itself should run on any platform OpenOffice.org runs on, but it has only been built on Ubunutu.

This example is originally based on [instructions found here](http://www.biochemfusion.com/doc/Calc_addin_howto.html)

Here's the [original blog post](http://www.enigmacurry.com/2009/12/13/writing-an-openoffice.org-calc-extension-in-python) 
where this extension was initially announced.

Building on Ubuntu
------------------

On Ubuntu, you must have `openoffice.org-dev` installed

 * `sudo apt-get install openoffice.org-dev`

Edit the Makefile to represent the OpenOffice.org development environment on your system. 
It should already be setup for the default in Ubuntu 9.10.

Run `make` in the src directory and SpotMetal.oxt should be built.

Example Usage
-------------

Once the plugin is installed (Tools->Extension Manager..), you have two new Calc functions available:

SPOTMETAL, which takes two arguments:

 * metal - Which metal you want to look up. Can be one of "gold", "silver", "platinum", or "palladium"
 * bidAsk - Whether you want the bid or the ask price. Can be either "bid" or "ask".

SPOTREFRESH, forces a refresh of the spot metal prices. Otherwise the values will get automatically refreshed every 5 minutes.

There is an example spreadsheet included (MetalTrackerExample.ods) that shows a sample gold and silver investment portfolio.
This example spreadsheet has a button to refresh the spot price, which itself is dependant on a OpenOffice.org Basic macro called doReCalculate.

You can view this macro by opening MetalTrackerExample.ods and going to `Tools->Macros->Organize Macros->OpenOffice.org Basic` inside 
`MetalTrackerExample.ods->Standard->SpotMetal->doReCalculate`
