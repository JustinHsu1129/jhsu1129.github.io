---
permalink: /
title: "Justin Hsu"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

I am a fourth year Electrical Engineering student at UC Davis with plans to pursue a Master degree in electrical engineering. I am broadly interested in physical design and VLSI. I am particularly interested in accelerator design for machine learning algorithms and low power IC design. My work focuses on the intersection between computer architecture and physical implementation. I am driven by the challenge of designing domain specific architectures, and specifically aiming to achieve maximum performance in a low power package.

Work Experience
======
1. RTL Design Engineer-Lotus Communication Systems
* Using the Xilinx Zynq 7000 SoC, I designed and implemented a digital FIR high pass and bandpass filter for cleaning recieved signals. Through Matlab simulation I found the necessary weights required to perform the digital filtering, and implemented the filters using verilog. I took advantage of the parallelism available on an FPGA-using a 4 stage pipelined transpose form filter.
* My final project was designing and implementing a cascaded integrator-comb decimation filter in Verilog designed for resource constrained FPGA environments. The architecture features automated bit-growth calculation and pipelining. Additionally, I used scalable parameterization when designing this module so this design could be reused across different projects. Lastly, numerous architectural decisions were made in order to implement the CIC filter to be completely multiplier free.

2. PCB Design Engineer-Lotus Communication Systems
* I designed a 4 layer PCB for a high frequency (~10GHz range) mixed signal two channel block up/down converter from schematics to physically soldering the components onto the board. Designing the schematics from OrCad, I was a key contributor to parts selection, and managed the bill of materials for sourcing availability. After, I designed the PCB using PADS. I carefully implemented a split grounding scheme and carefully managed return paths to prevent noise leakage from the digital blocks from coupling into the RF front end.
* I designed multiple sub-modules of the PCB, including a custom loop filter, digital microcontroller control block, and RF block. This modular design strategy allowed more effective isolation of critical RF signal paths, and greatly helped when designing the power and ground planes.

Senior Design Project-Live Video Feed Edge Detection Accelerator
======
My senior design project involves using an FPGA to design an accelerator for a live video feed edge detection algorithm, taking advantage of hardware parallelism for calculating gaussian blur and Sobel gradient. Additionally utilizing the onboard CPU to compute Hysteresis edge tracking through an algorithm written in C.

Site-wide configuration
------
The main configuration file for the site is in the base directory in [_config.yml](https://github.com/academicpages/academicpages.github.io/blob/master/_config.yml), which defines the content in the sidebars and other site-wide features. You will need to replace the default variables with ones about yourself and your site's github repository. The configuration file for the top menu is in [_data/navigation.yml](https://github.com/academicpages/academicpages.github.io/blob/master/_data/navigation.yml). For example, if you don't have a portfolio or blog posts, you can remove those items from that navigation.yml file to remove them from the header. 

Create content & metadata
------
For site content, there is one Markdown file for each type of content, which are stored in directories like _publications, _talks, _posts, _teaching, or _pages. For example, each talk is a Markdown file in the [_talks directory](https://github.com/academicpages/academicpages.github.io/tree/master/_talks). At the top of each Markdown file is structured data in YAML about the talk, which the theme will parse to do lots of cool stuff. The same structured data about a talk is used to generate the list of talks on the [Talks page](https://academicpages.github.io/talks), each [individual page](https://academicpages.github.io/talks/2012-03-01-talk-1) for specific talks, the talks section for the [CV page](https://academicpages.github.io/cv), and the [map of places you've given a talk](https://academicpages.github.io/talkmap.html) (if you run this [python file](https://github.com/academicpages/academicpages.github.io/blob/master/talkmap.py) or [Jupyter notebook](https://github.com/academicpages/academicpages.github.io/blob/master/talkmap.ipynb), which creates the HTML for the map based on the contents of the _talks directory).

**Markdown generator**

The repository includes [a set of Jupyter notebooks](https://github.com/academicpages/academicpages.github.io/tree/master/markdown_generator
) that converts a CSV containing structured data about talks or presentations into individual Markdown files that will be properly formatted for the Academic Pages template. The sample CSVs in that directory are the ones I used to create my own personal website at stuartgeiger.com. My usual workflow is that I keep a spreadsheet of my publications and talks, then run the code in these notebooks to generate the Markdown files, then commit and push them to the GitHub repository.

How to edit your site's GitHub repository
------
Many people use a git client to create files on their local computer and then push them to GitHub's servers. If you are not familiar with git, you can directly edit these configuration and Markdown files directly in the github.com interface. Navigate to a file (like [this one](https://github.com/academicpages/academicpages.github.io/blob/master/_talks/2012-03-01-talk-1.md) and click the pencil icon in the top right of the content preview (to the right of the "Raw | Blame | History" buttons). You can delete a file by clicking the trashcan icon to the right of the pencil icon. You can also create new files or upload files by navigating to a directory and clicking the "Create new file" or "Upload files" buttons. 

Example: editing a Markdown file for a talk
![Editing a Markdown file for a talk](/images/editing-talk.png)

For more info
------
More info about configuring Academic Pages can be found in [the guide](https://academicpages.github.io/markdown/), the [growing wiki](https://github.com/academicpages/academicpages.github.io/wiki), and you can always [ask a question on GitHub](https://github.com/academicpages/academicpages.github.io/discussions). The [guides for the Minimal Mistakes theme](https://mmistakes.github.io/minimal-mistakes/docs/configuration/) (which this theme was forked from) might also be helpful.
