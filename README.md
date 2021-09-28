# espiownage



> Ownage of ESPI image inference. (Pronounced like "espionage" but with a little "own" in the middle.) 

This code accompanies the paper submission [**"espiownage:Tracking Transients in Drum Strikes Using Surveillance Technology"**](https://www.dropbox.com/s/30nqyl0srekmu0s/steelpan_neurips_2021.pdf?dl=0) for the [NeurIPS 2021](https://nips.cc/Conferences/2021/) workshop on [Machine Learning and the Physical Sciences.](https://ml4physicalsciences.github.io/2021/) 

This study consists of 3 models:  Two that go together (a bounding box detector that feeds cropped images into an antinode ring-counter) and another complements them (an image sementation code we use for regression by scaling the final activation of a "one-class" model.)


All this documentation is fully executable, either locally or on Colab. This is made possible by [nbdev](nbdev.fast.ai), the development system that enabled us to stay organized and do this project in only 18 days! 


These pages are fully anonymized as are all the links that are used.  *Note that there is a "real" espiownage repo so don't go looking for that.*  Pending successful review of the paper, this repository will be redirected to the non-anonymous version.

## Install

### Preliminaries

Ubuntu (& probably other Linuxes):
```bash
sudo apt-get install python3-tk
```

Mac (with [Homebrew](https://brew.sh/))
```bash
brew install python-tk
```

Then on all systems, let's set up a virtual environment called `espi`. 
I like to put my environments in `~/envs`:

```
mkdir ~/envs; python3 -m venv ~/envs/espi; source ~/envs/espi/bin/activate
```
And then you want/need to update `pip` in case it gave you an ancient version:

```bash
python3 -m pip install pip --upgrade
```

### Pip install

```bash
pip install espiownage
```
Note: the requirements on this package follow a "kitchen sink" approach so that everything a student might need gets installed, e.g. `jupyter` and more. (And `wheel` because it speeds up the installations...I think.)

## How to use

If you're reading this, you probably have access to the "real" data, which sits (on my machine) in `~/Dropbox/Data/espiownage-data`.  So `cd` to that directory, i.e.,
```
$ cd ~/Dropbox/Data/espiownage-data
```
...(or whereever you've got it) for what follows. 

**AND THEN**, so we don't "clobber" each other's work, make *your own copy* (~17MB) of the main `annotations` directory, as in append your last name (student, student, student, etc):

```bash
cp -r annotations annotations_yourlastname
```
and then we'll each edit our own copy just to avoid...confusion. 
> *Note:If you don't have access to the real data,* you can still grab the [fake SPNet data](https://zenodo.org/record/4445434) and then, for each of those datasets: Move (or symlink) all the images to a directory called `images/`, and all the `.csv` files to a directory called `annotations/`, and proceed.

## Console Scripts
See the separate page on console scripts

## Contributing / Development 

You'll want to install more things:

```bash
pip install nbdev twine 
```

Fork this repo.  When you want to update your repo, one macro does it all (see `Makefile`):
```bash
make git_update
```

## Asides

### Handy tips for students
I can never remember how to start up virtual environments / or I don't *want* to remember. So in my `~/.bashrc` file (you may have a `~/.zshrc`) I put in a line where I define an alias/function I call `gimme`, that reads like so:
```bash
gimme() { source ~/envs/"$1"/bin/activate;  }
```
(note that in order for this alias to be recognized, you need to either logout and log back in or else run `$ source ~/.bashrc`)

Then when I want to load environment like `espi` I just type...
```bash
gimme espi
```

