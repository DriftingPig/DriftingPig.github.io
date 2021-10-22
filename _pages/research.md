---
permalink: /research/
title: "Research"
author_profile: true
layout: archive
---

{% include base_path %}

Image simulation
======
Image simulation focuses on the problem of imaging systematics:  false fluctuations in the target galaxy density arising from imperfect measurements in the imaging surveys. Imaging surveys provide the target information for spectroscopic observations.  Galaxies and other objects such as QSOs (Quasars) are selected  from  the  imaging  catalog  using  mainly  flux  and  color  information. These measurements are contaminated by numerous effects such as galactic extinction, the noise level of the images, observing conditions, etc. All these systematic effects need to be understood and corrected for when analyzing the data. I have developed a novel method to correct imaging systematics for ELGs (emission line galaxies) and LRGs (Luminous Red Galaxies). The idea of this method is to use image simulations to study galaxy tracers. I simulate realistic galaxies on pixelated images, add these galaxies to real images, and run the standard image reduction pipeline to recover a catalog of these input simulated galaxies. I showed that the output simulated galaxies catalog shares the same false trends as real galaxies. Using the image simulations provide a first principle manner of predicting the contaminated signal. Results from image simulation are vital for future cosmology measurements: Since we have entered the regime of precision cosmology, decoupling physical signals and measurement errors is a key ingredient for a precise, convincing measurement. 



Pipeline Development
======
My work is based on the [Legacysurvey](https://www.legacysurvey.org/) and its image reduction pipeline [Legacypipe](https://github.com/legacysurvey/legacypipe). The Legacysurvey catalogs are used to select targets for DESI to measure spectroscopic redshifts. In our image simulation pipeline, simulated sources are added to the image on a per CCD (individual exposure) level. The catalog of measured properties of simulated sources is obtained by matching to the location of their injection. We are thus provided a mapping between true and observed properties. Our pipeline is able to produce an output simulated galaxies catalog using only a fraction of computing resources that is used by the standard image reduction pipeline, while preserving the same precision level. It is also capable of simulating galaxies in both optical (g,r,z) bands and infrared (WISE, Wide-field Infrared Survey Explorer) bands. 


![Here is a demenstration of pipeline diagram](/images/IS-diagram.png)

The simulated sources are convolved with the local PSF (point spread function) at that location. The modified image sets are then processed in the same way as a normal image reduction run. The simulation pipeline is composed of two stages: The optical band stage and the infrared band stage. The optical band consists of images taken from ground based surveys. Sources in optical bands are less spread out (small PSF), and they are segmented into blobs. A blob is a contiguous pixel region of S/N>6. Only blobs containing simulated sources are fitted to get precise information for the sources inside. Fitting selected blobs only saves computing time. Detected sources are fitted to obtain a flux value for each band, as well as source location and shape. The information of source location and shape then becomes input for infrared band imaging. Infrared band images are from WISE (Wide-field Infrared Survey Explorer). Wise is a space telescope with all sky coverage. The small 0.4 m aperture of the telescope results in a much larger PSF for the infrared band, meaning that blending is more severe. Due to this reason, the sources on WISE image are measured with forced photometry: the source location and shape information are fixed values, and the only free parameter is the flux for each source. These fixed values are taken from optical band fittings. Since we do not have source information outside our interested blobs, we utilize dr9 catalog (the 9th data release of Legacysurvey), and the out-of-blob region sources are set to dr9 sources. 

![Here is a demenstration of pipeline diagram](/images/shape-debiasing.png)
 
ELG
======
We apply this method for eBOSS ELGs(emission line galaxies). See details in [this paper](https://academic.oup.com/mnras/article/499/3/3943/5909048?login=true)

LRG
======
We also apply this method to DESI LRGs (Luminous Red galaxies). Details coming soon! 


  





  





  



