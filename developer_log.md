# Create fake landscapes for Linkedin 

### originally starting out with basic classic paintings

following introducation guide: https://medium.com/jovianml/generating-art-with-gans-352ceef3d51f

getting torchvision was a pain with my current anaconda set up, recomend using:
conda install pytorch torchvision, instead of using the GUI conda interface. 

no other issues importing other modules 

*----------------------*------------*
| torchvision.__version__ = '0.8.2' |
| torch.__version__ = '1.7.1'       |
| MacOS Catalina version = '10.15.7'|
| pytorch version = '1.7.1'         |
| python version = '3.8_0'          |
*----------------------*------------*


##### issue 01: 
the given dataset that this guide walks through with, you are unable to download the data. It throws a too many requests error. https://www.kaggle.com/ikarus777/best-artworks-of-all-time?select=artists.csv

##### solution 01: 
to download kaggle datasets you need to first log into kaggle. At this time I had looked around at other datasets and found an okay one with around 4k+ photos of landscapes, so I will be using this dataset instead of the art one. https://www.kaggle.com/arnaud58/landscape-pictures?select=00000000_%286%29.jpg (bad naming conventions)

##### issue 02: 
torchvision.datasets.ImageFolder unable to find folder directory 

##### solution 02: 
function needs full directory name not just '../somedir/somedir'

##### issue 03:
torchvision.datasets.ImageFolder is only getting 6 of the 4319 images

##### solution 03: 
archive folder needed to be placed within a new folder inside of our working directory. The ImageFolder is looking for an folder with images in it, it does not want to be handed the images directly.

--> now we are back on track, note: landscapes rescaled to 64x128

##### issue 04: 
when landscapes are scaled to 64x128 the fit method does not like it because the generative and discriminator networks are not the same size... I do not want to debug this right now so I changed it back to 64x64

##### solution 04:
fix more in detail at a later time till then, 64x64

--> average interval time of fit, 8 mins. 150 intervals of fit

*----------------------*--------*
| est. completion time | 20 hrs |
| actual time          |    hrs |
*----------------------*--------*

Once this is trained we will be able to see how a bunch of different landscapes are formed through the different intervals of the gan. (my hopes are not strong with this one) 

* the GAN has been running for 2 hours without producing a new result -.-

### What needs to be done?

* the GAN generator and discriminator networks need to be modified to take in a landscape (rectangle) instead of a square.

* additionally the fit method should be modified to not take as long.

readings: 

