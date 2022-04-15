## Problem Statement

Earth's man-made satellite ecosystem is constantly evolving in terms of new payloads and debris present.  With a marked increase in space exploration in the last decade both in terms of governments and private corporations, it is important to understand the potential challenges that this environment faces with further expansion.  As more launches occur not only will more debris be present, but more payloads will cause strain on certain altitudes and inclinations of Earth’s orbits.  Given the nature that some orbits are advantageous or needed for certain satellite functionality, it is crucial to determine the risks of collision between orbiting objects.  The purpose of this study is to model close approaches between objects to further illuminate the hazards that active orbiting payloads face and additionally the initiatives potentially needed to ensure future cooperation and use of Earth’s orbits.

## Executive Summary

The scope of the current model is focused on low earth orbit.  From the Space-Track data set, most satellites that are categorized as a payload (a satellite that was placed in orbit via a launch vs debris or a launch vehicle stage that is in orbit) are in low earth orbit.  This region is typically defined as objects within 2000 km altitude above earth.  Satellites in this region have highly circular orbits and can take as little as 90 minutes to circle the Earth.  There is also a significant number of other objects being tracked in this section of Earth’s orbital regions.

The SpaceX Starlink micro satellite constellations have many satellites in close proximity regarding not only altitude, but also orbital inclinations.  Due to the goal of creating a network of satellites that can provide high speed internet to many regions of the world via wireless connection, this requires many orbiting vehicles so that coverage regions always have a possible uplink that is available.  While this brings up the question of what will happen if other entities want to pursue a similar venture (there is only so much real estate above Earth), this provides a very good test bench for a collision model because their satellites make close approaches very often.  

The model is currently capable of simulating ~2000 orbiting elements and checking for close approaches at a rate of 10 iterations per second.  In the current form, this means that if one wanted to simulate 10 days of close approaches it would take approximately one day.  The output is in the form of satellite indices (allowing for calling back into the data-frame for further trajectory modelling), the time of closest approach between the two satellites, and the distance of the approach.  

Additions that need to be made to this model would be to improve the iteration run time overall, but also add an element to increase the collision distance accuracy.  The objects in low earth orbit can be travelling ~7 km/s, and with the current model timestep this means that the close approach distances are not truly the satellites closest approach at the simulation times.  What is needed is a function that iteratively time steps around the close approach detected and returns a more accurate value.  This can potentially be added with little additional computation cost as sgp4 computations are very fast.

## Notebook Overview

EDA_CAP_SAT : Exploratory data analysis of the satellite data pull

EDA_Post_Model_Compare : A comparison of the model runs regarding close approaches

Cap_sat_production_1.0_LEO : low earth orbit simulation, including STARLINK but not checking between them

Cap_sat_production_1.0_MG : Medium and GEO simulation with debris included

Cap_sat_production_1.0_gif : they say a picture is worth a 1000 words, so a .gif is 1000 * n_frames of words


## Data Dictionary

Information regarding data types via Space Track website.

https://www.space-track.org/documentation#legend

https://www.space-track.org/documentation#tle
