<img src="chartpy_logo.png?raw=true" width="300"/>

# [chartpy](https://github.com/cuemacro/chartpy)

chartpy creates a simple easy to use API to plot in a number of great Python chart libraries like plotly (via cufflinks), bokeh and matplotlib,
with a unified interface. You simply need to change a single keyword to change which chart engine to use (see below), rather than having
to learn the low level details of each library. I've also created new stylesheets and formating to ensure that the default matplotlib
styling looks more modern using Open Sans font.

*Contributors for the project are very much welcome, sell below!*

```
chart = Chart(df=df, chart_type='line', style=style)

# we now plot using multiple plotting libraries, with the same dataframe
chart.plot(engine='matplotlib')
chart.plot(engine='bokeh')
chart.plot(engine='plotly')
```

I had previously written the open source PyThalesians financial library. This new chartpy library has some similar functionality to the chart
part of that library. However, I've totally rewritten the API to make it much cleaner and easier to use. It is also now a fully
standalone package, so it'll be easier to use for both non-financial and financial applications. It also has many more features including subplots 
and much more.

At present chartpy supports several types of plots
* line (bokeh, plotly and matplotlib)
* bar (bokeh, plotly and matplotlib)
* scatter (bokeh, plotly and matplotlib)
* bar horizontal (matplotlib and plotly)
* heatmap (matplotlib and plotly)
* surface (plotly)
* map plots (plotly)
* looking to add more (any requests?)

# VisPy

There is also very early support for line charts generated by [vispy](http://vispy.org/), which allows for GPU accelerated plotting in Python.
However, at present the wrapper doesn't yet support plotting of dates (these are ignored when plotting).

There is a big speed improvement in using the VisPy wrapper if you are plotting many millions of points (with a small number of points
matplotlib seems quicker). Installation instructions for VisPy are [here](http://vispy.org/installation.html). By default,
chartpy will install the latest release version, but you find it necessary to use the most up to date development version of VisPy

Other points to note
* Please bear in mind at present chartpy is currently a highly experimental alpha project and isn't yet fully 
documented
* Uses Apache 2.0 licence

# Gallery

Doing plots in multiple libraries by simply changing a keyword, from the Jupyter notebook.

<img src="https://github.com/cuemacro/chartpy/blob/master/chartpy_examples/screenshot.png?raw=true" width="543"/>

Create subplots with minimal extra coding (see examples/subplot_examples.py)

<img src="https://github.com/cuemacro/chartpy/blob/master/chartpy_examples/subplot.png?raw=true" width="543"/>

Do surface plots (plotly only at present - see examples/surface_examples.py)

<img src="https://github.com/cuemacro/chartpy/blob/master/chartpy_examples/volsurface.png?raw=true" width="543"/>

Do bar horizontal plots (matplotlib and plotly - see examples/chart_demo.py)

<img src="https://github.com/cuemacro/chartpy/blob/master/chartpy_examples/barh.png?raw=true" width="543"/>

Create heatmaps (matplotlib and plotly - see examples/chart_demo.py)

<img src="https://github.com/cuemacro/chartpy/blob/master/chartpy_examples/heatmap.png?raw=true" width="543"/>

<img src="https://github.com/cuemacro/chartpy/blob/master/chartpy_examples/plotlyheatmap.png?raw=true" width="543"/>

Create HTML webpages (using Canvas class - see examples/canvas_demo.py) - using mixture of plots (plotly, bokeh & matplotlib), tables
and text, with just a few lines of Python! The HTML file can then be uploaded to a webserver for display (or sent around by e-mail etc)

<img src="https://github.com/cuemacro/chartpy/blob/master/chartpy_examples/canvas.png?raw=true" width="543"/>

# Requirements

Major requirements
* Required: Python 3.4, 3.5
* Required: pandas, matplotlib, plotly, cufflinks, bokeh, numpy etc.

# To install Open Sans font

My chartpy stylesheet for matplotlib uses the free Open Sans font. For it to display properly you need to install Open Sans font
on your computer
* First download font from https://www.fontsquirrel.com/fonts/open-sans
* Windows: Install font by dragging to Windows/fonts folder
* Windows: Reset matplotlib font cache (delete file eg. c:/users/username/.matplotlib/fontList.py3k.cache
* On Mac OS X/Linux procedure for installing fonts is different


# Installation

You can install the library using the below. After installation:
* Make sure you edit the ChartConstants class for the correct Plotly API and Twitter API keys

```
pip install git+https://github.com/cuemacro/chartpy.git
```

# Why did I write chartpy?

There are many good charting libraries. However, they all have different APIs. It took me a lot of time to learn a new API,
for each new plotting library I wanted to use. I ended up writing chartpy to abstract away all this complexity, so I could
concentrate on analysing data, rather than getting caught up in complex API visualisation calls. Rather than
having to totally edit my code each time, a single keyword is enough to switch between for example plotly and matplotlib.

I've also tried to design the library so that adding a new plotting engine is fairly straightforward (extend EngineTemplate
and edit the get_engine method in Chart), so it's basically future proof for whatever new chart libraries come along, with
relatively small changes to your code base.

# Contributors

Contributors are always welcome for finmarketpy, findatapy and chartpy. If you'd like to contribute, have a look at
[Planned Features](https://github.com/cuemacro/finmarketpy/blob/master/PLANNED_FEATURES.md) for areas we're looking for help on. Or if you have any ideas for improvements
to the libriares please let us know too!

# chartpy examples

In chartpy/examples you will find several demos

# Release Notes

* No formal releases yet

# Coding log

* 26 Mar 2018 - Various bug fixes
* 19 Feb 2018 - Support for Python 2.7 and Plotly engine now supports dash
* 21 Dec 2017 - Added webgl Plotly charts & other Plotly parameters
* 15 Nov 2017 - Fixed bug when plotting time series with DatetimeIndex and newer matplotlib
* 10 Oct 2017 - Added flag to works in Bokeh 0.12.9
* 18 Sep 2017 - Fixed plotting DataFrame with DatetimeIndex with Bokeh
* 05 Jul 2017 - Fixed PLANNED_FEATURES.md link
* 03 May 2017 - Added more on contributors
* 24 Apr 2017 - Added extra xkcd example
* 19 Feb 2017 - Added simple animations for matplotlib
* 16 Feb 2017 - Added VisPy support for plotting and added demo example
* 11 Feb 2017 - Added chartpy logo
* 05 Feb 2017 - Fixed x-axis date formatting issue with matplotlib wrapper
* 02 Feb 2017 - Added page title to Canvas and starting to add PDF support for canvas
* 27 Jan 2017 - Added save_fig attribute in style
* 23 Jan 2017 - Moved examples folder
* 30 Nov 2016 - Added skeleton for bqplot (not implemented yet)
* 17 Oct 2016 - Added grid flags for bokeh, plotly and matplotlib, improved formating on printing dataframes
* 14 Oct 2016 - Fixed missing stylesheets in package setup
* 12 Oct 2016 - Fixed handling of auto generated filenames
* 11 Oct 2016 - Changed handling of auto generated filenames
* 10 Oct 2016 - Added xkcd style plots for matplotlib
* 07 Oct 2016 - Added .idea to .gitignore
* 06 Oct 2016 - Added support for secondary y-axis in Plotly
* 29 Sep 2016 - New webpage_examples notebook to illustrate creating chart webpages
* 26 Sep 2016 - Added thin margin setting for Plotly
* 25 Sep 2016 - Added Canvas method to easily create webpage reports with charts
* 23 Sep 2016 - Fixed deprecated method for uploading to Twitter
* 03 Sep 2016 - Added horizontal bars and heatmap for matplotlib and plotly
* 28 Aug 2016 - Added explanation of why chartpy?
* 20 Aug 2016 - Added Plotly default palette, surface examples
* 19 Aug 2016 - Added HTML examples for bokeh & plotly, subplotting for bokeh, plotly & matplotlib (with subplot_examples)
* 17 Aug 2016 - Uploaded first code

End of note
