# Bike Share Prediction

This is an internship project from [iNeuron.ai](https://ineuron.ai/) related to Bike share prediction problem statement.

## Problem statement

[Reference link](https://drive.google.com/file/d/1ql9wJpcfx794zSgTBM-5LqH5k88ZZ5fM/view)

**Bike sharing systems** are a new generation of traditional bike rentals where the whole process from membership, rental and return back has become automatic. Through these systems, users are able to easily rent a bike from a particular position and return back at another position. Currently, there are about over 500 bike-sharing programs around the
world which is composed of over 500 thousand bicycles. Today, there exists great interest in these systems due to their important role in traffic, environmental and health issues. Apart from interesting real-world applications of bike sharing systems, the characteristics of data being generated by these systems make them attractive for the research.

The goal here is to build an _end-to-end regression task_ to **predict bike rental count hourly** or daily based on the environmental and seasonal settings. Here the user will provide the data and the result will be given by the best performing hyper-tuned Machine Learning model. The user will also get privileges to choose the deployment options.

## Dataset

[Link](https://archive.ics.uci.edu/ml/datasets/Bike+Sharing+Dataset)

Bike-sharing rental process is highly correlated to the environmental and seasonal settings. For instance, weather conditions, precipitation, day of week, season, hour of the day, etc. can affect the rental behaviors. The core data set is related to the two-year historical log corresponding to years 2011 and 2012 from Capital Bikeshare system, Washington D.C., USA which is
publicly available in http://capitalbikeshare.com/system-data. We aggregated the data on two hourly and daily basis and then
extracted and added the corresponding weather and seasonal information. Weather information are extracted from http://www.freemeteo.com.

This dataset contains the hourly and daily count of rental bikes between years 2011 and 2012 in Capital bikeshare system with the corresponding weather and seasonal information.

- Number of instances: 17389
- Number of attributes: 16
- Attribute characteristic: Integer, Real

### Attribute Information:

Both `hour.csv` and `day.csv` have the following fields, except `hr` which is not available in `day.csv`

- instant: record index
- dteday : date
- season : season (1:winter, 2:spring, 3:summer, 4:fall)
- yr : year (0: 2011, 1:2012)
- mnth : month ( 1 to 12)
- hr : hour (0 to 23)
- holiday : weather day is holiday or not (extracted from [Web Link](http://dchr.dc.gov/page/holiday-schedule))
- weekday : day of the week
- workingday : if day is neither weekend nor holiday is 1, otherwise is 0.
- weathersit :
  - 1: Clear, Few clouds, Partly cloudy, Partly cloudy
  - 2: Mist + Cloudy, Mist + Broken clouds, Mist + Few clouds, Mist
  - 3: Light Snow, Light Rain + Thunderstorm + Scattered clouds, Light Rain + Scattered clouds
  - 4: Heavy Rain + Ice Pallets + Thunderstorm + Mist, Snow + Fog
- temp : Normalized temperature in Celsius. The values are derived via (t-t_min)/(t_max-t_min), t_min=-8, t_max=+39 (only in hourly scale)
- atemp: Normalized feeling temperature in Celsius. The values are derived via (t-t_min)/(t_max-t_min), t_min=-16, t_max=+50 (only in hourly scale)
- hum: Normalized humidity. The values are divided to 100 (max)
- windspeed: Normalized wind speed. The values are divided to 67 (max)
- casual: count of casual users
- registered: count of registered users
- cnt: count of total rental bikes including both casual and registered

## Setup a new virtual environment

I'm using conda (from Anaconda.org) to manage my virtual environments.

- To create a new virtual environment
  ```shell
  $ conda create -n ineuron-bike-share-env
  ```
- Activate `ineuron-bike-share-env` virtual environment
  ```shell
  $ conda activate ineuron-bike-share-env
  ```
- Install Python v3.8.6 in the new environment
  ```shell
  $ conda install -y python==3.8.6
  ```
- Install Numpy
  I'm using MacOS M1 chip and conda miniforge version for Numpy still doesn't work for me. So I've to manually install it from Apple wheel.
  ```
  $ wget https://github.com/apple/tensorflow_macos/releases/download/v0.1alpha0/tensorflow_macos-0.1alpha0.tar.gz
  $ tar xvf tensorflow_macos-0.1alpha0.tar.gz
  $ cd tensorflow_macos/arm64
  $ /opt/homebrew/Caskroom/miniforge/base/envs/ineuron-bike-share-env/bin/pip install --upgrade --no-dependencies --force numpy-1.18.5-cp38-cp38-macosx_11_0_arm64.whl
  ```
- Install other required libraries
  ```shell
  $ conda install -n ineuron-bike-share-env pandas scikit-learn matplotlib seaborn
  ```

## Data exploration

We are required to explore the dataset to deeply understand the data and if we can visualize patterns from the data. Following is the notebook:

- [eda.ipynb](notebooks/eda.ipynb)
