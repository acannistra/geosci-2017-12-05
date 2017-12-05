# Process Discussion: Two (Three?) Geospatial Analysis Challenges
**[UW eScience Python for Geosciences Seminar, 2017-12-05.](https://github.com/uwescience/Python-for-geosciences/blob/master/tcannistra_20171205)**

## Abstract:
A wide variety of tools exist for the processing of geospatial data in Python. I intend with this brief talk to collaboratively develop two pipelines for geospatial data assimilation and visualization through one or two specific vignettes, chosen from a United States national public lands demography project and a study into worldwide ecological impacts on mining. These are side projects and largely undeveloped, but demonstrate some tools that I find quite useful in quickly extracting and visualizing useful insight from geospatial data in Python, and that hopefully will engage the group and invite sharing of different methods among us.

## Vignette 1: U.S. Public Lands Access [<img src="https://assets-cdn.github.com/images/modules/logos_page/GitHub-Mark.png" height=25>](https://github.com/acannistra/parkdistance)

__Problem:__ What effect will executive action on the extent and location of American public lands have on American access to public land across demographics? 

__Deliverables:__

1. Two Maps: one demonstrating current state of access to public lands (across types? parks, forests, wilderness) across CONUS, and another demonstrating the same but with some reduction/removal plan implemented. 
1. Some metric of access broken down by population demographics: are certain demographics proportionally affected by these changes? What's a meaningful metric?
1. Interactive web presence allowing an individual to develop their own "executive action" scenario and observe the effects on access. 


__Current Progress (<small>see gh link above</small>)__:
<details>
<summary>A nice image with as-the-crow-flies distance to parks/forests/wilderness. (click)</summary>
<img src="https://github.com/acannistra/parkdistance/blob/master/conus_distance_small.png?raw=1"></img>
</details>



__Extensions:__

* "Access" seems like an interesting but not totally relevant metric. Some sort of economic analysis seems interesting too, but doesn't have as much of a 
geospatial assimilation component. 
* Crow-flies distance seems unsuitable, but how to do anything else?


## Vignette 2: Lake Algae Classification with Sentinel-2 [<img src="https://assets-cdn.github.com/images/modules/logos_page/GitHub-Mark.png" height=25>](https://github.com/acannistra/lakeclass)

__Problem:__ Toxic algal/cyanobacterial blooms in lakes are a threat to human and nonhuman life; their identification is expensive (requires a lab) so it would be great to have a remotely-sensed alternative (not the first to have [thought of this](https://cfpub.epa.gov/si/si_public_record_report.cfm?dirEntryId=337171)). 

__Deliverables__:

1. A trained classifier which, given an image of a lake, can return a probability of an algae bloom in that lake. 
2. A pipeline for the real-time acquisition of lake imagery. 
3. A web interface for this classifier + warning service for popular lakes. 

__Current Progress__:

<details>
<summary>Barebones Sentinel-2 polygon extraction + images(click)</summary>
[`sentinel-extract.py` ](https://github.com/acannistra/lakeclass/blob/master/sentinel-extract.py) script and [notebook](https://github.com/acannistra/lakeclass/blob/master/experiments/extract-poly-clean.ipynb) gets us extracted images of any lake where a shape file of its boundary exists.

We've gotten about 1000 images for lakes in Washington this way, up in S3.
</details>

<details>
<summary>A pipeline for merging Washington Dept. of Ecology lake measurements with corresponding nearest satellite imagery. (click)</summary>
[This notebook](https://github.com/acannistra/lakeclass/blob/master/experiments/generate-extract-request.ipynb) is responsible for generating the requests to the image access pipeline---is basically just a join on 2 tables. 
</details>

<details><summary>A bunch of images</summary>
<img width="100%" src="https://www.dropbox.com/s/z8ye7p5dvjm5946/pugetlargegood.png?raw=1"></img>
<img width="100%" src="https://www.dropbox.com/s/f0e9fv6mvbev0xy/greatwa2.png?raw=1"></img>
<img width="100%" src="https://www.dropbox.com/s/imu91ifzj1lvaeb/vsmall.png?raw=1"></img>
</details>

Issues have been that the extracted images are largely quite low-quality, unsuitable for training a model. I paused this because there was much work to do and not quite enough time to get it done for a quarter project!

## Vignette 3: Mining Demographics [<img src="https://assets-cdn.github.com/images/modules/logos_page/GitHub-Mark.png" height=25>](https://github.com/acannistra/mining)

__Problem__: How are mines spatially and demographically distributed? We fight against extractive industries in special places, but where do they go when we win? How does (more treatment in [this draft](https://blog.anthonycannistra.com/not-here-but-where-106d970f61e2)) 

