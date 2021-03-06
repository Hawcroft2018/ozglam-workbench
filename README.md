# OzGLAM data workbench

**Please note this is experimental and unfinished. I'm still learning about the capabilities of Jupyter. Things might change radically!**

This is a collection of [Jupyter](http://jupyter.org/) notebooks to help you explore and use data from Australian GLAM institutions. It's aimed at researchers in the humanities, but will include tutorials of more general interest -- such as an introduction to the Trove API.

Over the past decade I've created and shared a wide variety of digital tools, examples, tutorials, and datasets. Some like [QueryPic](http://dhistory.org/querypic/) and [TroveHarvester](http://timsherratt.org/digital-heritage-handbook/docs/trove-newspaper-harvester/) are fairly polished and well documented. Others are just fragments of code. All of them are intended to support research into our rich cultural collections.

But even though something like the TroveHarvester is pretty easy to use, it does require a bit of set-up, and I've been very aware that this can be a barrier to people starting their explorations. I created the [dhistory](http://dhistory.org/) site many years ago to provide the foundation for a digital workbench, but I couldn't quite achieve what I wanted -- tools that were easy to use and required minimal setup, but also tools that exposed their own workings, that inspired novice users to question and to tinker.

So here we are. My plan is to use Jupyter, GitHub, [Binder](https://mybinder.org/), and [Docker](https://www.docker.com/) to bring together all those tools, examples, tutorials, and datasets in a way that supports people's explorations through digital GLAM collections. I'm really excited, for example, that I can create a notebook that provides a deconstructed (or perhaps see-through) version of QueryPic -- that enables you to build, step by step, the same sort of visualisations, while learning about how it works. And at the end you can download the results as a CSV for further analysis. I love the way that Jupyter notebooks combine learning with real, live, digital tools and methods. You don't have to read a tutorial then go away and try to follow the instructions on your own. It's all together. Live code. Real research. Active learning.

Like most of my projects this is in itself an experiment. I'm still learning what's possible and what works. But I'm hopeful.

## Subject-specific workbenches

As well as this generic workbench, I'm creating a few subject-specific versions that come complete with pre-harvested data, ready to explore. So far there's:

* [Series in the National Archives of Australia relating to the White Australia Policy](https://github.com/wragge/ozglam-workbench-naa-wap)
* [Series in the National Archives of Australia with content recorded by the Australian Security Intelligence Organisation (ASIO)](https://github.com/wragge/ozglam-workbench-naa-asio)
* Records of Resistance (coming soon...)

## Potential uses

* **Research!** The workbench will include live working versions of tools like TroveHarvester and my assorted RecordSearch harvesters, as well as examples of how you can start analysing your results.
* **Education!** There'll be a tutorials with live, working code -- play with collections while picking up some Python.
* **Workshops!** No more battling with multiple operating systems and locked down computer labs (at least I hope so...).

## Current outline (this will change!)

    Introduction and table of contents
    Using the notebooks

    - Trove
        - Introduction to the Trove API
        - Making your first API request
        - Understanding zones
        - Getting records
        - More complex queries
        - Working with newspaper articles
        - Newspaper titles
        - Works and versions
        - Finding URLs
        - Finding thumbnails
        - Working with contributors

        - Trove cookbook
            - Exploring facets
            - DIY QueryPic
            - Harvesting front pages
            - Harvesting parliamentary press releases
            ...more

        - TroveHarvester
            - Using TroveHarvester to get newspaper articles in bulk
            - Exploring your TroveHarvester data
            - Analysing article texts
            ...more

    - RecordSearch
        - Getting data out of RecordSearch
        - Harvesting a series
        - Harvesting a search
        - Understanding functions
        - Analysing file titles
        ...more

    - CSV explorer
        - Dataset browser
        - CSV analyser
        - Harvesting from data portals
        ...more

    - More sections dealing with particular collections, datasets, or APIs

## Support me

If you think this is a worthwhile endeavour, feel free to [support me on Patreon](https://www.patreon.com/timsherratt).

----

## Using the workbench

### View the notebooks

If you just want to have a look around, you can browse the notebooks in this repository. Even better, you can [explore them using the Jupyter Project's Notebook Viewer](https://nbviewer.jupyter.org/github/wragge/ozglam-workbench/blob/master/1-Introduction-and-table-of-contents.ipynb). But these will be static, read-only, versions -- you won't be able to run any of the code.

### Use the notebooks online with MyBinder

The easiest way to use the notebooks is on MyBinder. Just click on the button!

[![Binder](https://mybinder.org/badge.svg)](https://mybinder.org/v2/gh/wragge/ozglam-workbench/master)

MyBinder launches the notebooks in a custom computing environment with all the software you'll need pre-installed. You can explore, harvest, and analyse cultural heritage data without ever leaving your web browser.

I've harvested thousands of Trove newspaper articles using MyBinder, but there are some limitations. The main one is that the environments it creates are only temporary. There's no way of saving your session and going back to it later. So if you harvest data, you'll need to download it before the session ends. But don't worry, I've provided a few handy tools to make downloading easy.

MyBinder sessions will also shut down after about 10 minutes of inactivity. So don't go and have lunch without making sure you've finished what you're doing.

### Run locally with Jupyter

If you have [Jupyter installed](http://jupyter.org/install) on your system, you can clone this repository and then run fire up the notebooks:


```
git clone https://github.com/wragge/ozglam-workbench.git
cd ozglam-workbench
jupyter notebook
```

The workbench will open in your browser.

### Run locally with Docker

I've created a Docker image that includes these notebooks and all the necessary software. Assuming you have [Docker installed](https://docs.docker.com/install/), just open up a terminal and run:

``` shell
docker run -it --name=Workbench -v MyData:/home/jovyan/data -v MyWorkbench:/home/jovyan/workbench -p 8888:8888 wragge/ozglam-workbench
```

This command downloads the image and builds a container to run the workbench. The `-v MyData:/home/jovyan/data` bit creates a persistent volume called `MyData` where any data you harvest will be stored. You can update the image, create new containers, and still access your data. Similarly, `-v MyWorkbench:/home/jovyan/workbench` creates a persistent volume to store the notebooks themselves. This means that any changes you make to the notebooks will also be stored independently of the container itself. This should give you a bit of flexibility in how you use the workbench, and allow you to customise it to your needs.

Once Jupyter starts up it'll display a url in the terminal that looks something like:

```
http://localhost:8888/?token=262718512d11cc3efcb1b2878f4jja9uca071924e328d554
```

Just copy and paste this into your browser to open the notebooks.

To restart the `WorkBench` container using the same data volumes:

``` shell
docker start -ai Workbench
```
