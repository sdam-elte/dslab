# Photometric redshift estimation

## Sloan Digital Sky Survey

The Sloan Digital Sky Survey (sometimes also called the Cosmic Genome Project) is a systematic photographic and specroscopic mapping of the extragalactic universe. During the first phase of the project, an imaging survey was conducted to photograph the sky in five optical wavelength band with a 120 megapixel camera. It was followed by a spectroscopic survey where more than 2 million objects, including more than a million galaxies were observed with a multi-fiber spectrograph.

The SDSS catalog (numerical parameters of the detected objects extracted from the multi-band images) is available as a relational database via SkyServer.

* Link to SDSS SkyServer: http://skyserver.sdss.org/

## Magnitudes

Luminosity $L$ is a primary intrinsic property of galaxies, it is the amount of energy emitted per second in a given wavelength range. Like power, it can be measured in W or erg s$^{-1}$ but astronomers prefer to express it in units of solar luminosity $L_{\textrm{Sol}}$, i.e. the luminosity of the Sun. The luminosity of the largest galaxies can be as high as $10^{12}$-$10^{14} L_\textrm{Sol}$. When brightness is measured from a distance, we measure flux instead of luminosity:

$$ F = \frac{L}{4\pi D_L}, $$

where $D_L$ is the _luminosity distance_ which has a special meaning in the expanding universe. Distances are measured through spectroscopic redshift which, in first order at very low redshifts yields a distance $D$ according to Hubble's law:

$$ c z = H_0 D, $$

where $H_0$ is the Hubble constant, $c$ is the speed of light and $z$ is the redshift.

Instead of expressing brightness as luminosity or flux, astronomers prefer the negative logarithmic magnitude system. The apparent magnitude $m$ of a galaxy is defined with its flux as

$$ m = -2.5 \log_{10} F + m_0, $$

where $m_0$ is a constant fixed by the _magnitude system_ used. in case of the _AB_ magnitude system of SDSS, it is set to be $m_0 = -48.6$ regardless of the bandpass filter used for the observation. The absolute magnitude $M$ of a galaxy could be defined similarily from luminosity, but astronomers use the traditional definition

$$ M = m - DM - K - A, $$

where $A$ is the foreground extinction, see later, and $DM$ is the _distance modulus_ defined as

$$ DM = 5 \log_10 D_L $$

and $K$ is the so called K-correction that comes from the fact that the spectra of distant galaxies are redshifted with respect to the bandpass filter used for the observation. Measuring the apparent magnitude of resolved sources in CCD images is rather arbitrary. Various method exists from which the so called Petrosian magnitudes are the best-suited to compare galaxies which appear different in size in images.

The term $A$ is a correction for foreground extinction (reddening) caused by the dust in our Galaxy. This value can be looked up for each filter of any magnitude system by using a dust map, but this value is also available in the SkyServer databae for every object.

The logaritm of flux ratios is called the color index. It is easy to see that the color index is the difference of to magnitudes measured in the corresponding filters:

$$ CI_{AB} = m_A - m_B. $$

An interesting property of the color index -- when neglecting K-correction -- is that it does not depend on the distance, since the distance moduli cancel out.

## Photometric redshift estimation

Hubble's law gives the distance in first order to galaxies of the nearby universe that are far enough for their recession velocity to be dominant over peculiar velocity:

$$ c z = H_0 D, $$

where $c$ is the speed of light, $z$ is the redshift, $H_0$ is the Hubble constant which is somewhere between $68$-$72~\textrm{km}~\textrm{s}^{-1}$. Redshift is measured by spectroscopic observations, a time consuming and expensive method due to the limited mirror size of the available telescopes. Even with the latest generation of fiber-fed spectrographs, only about a thousand spectra can be measured simultaneously. Comparing this with the typical minimum exposure time of 45 minutes and the 200 million relatively bright galaxies identified in the images photographed by the Sloan Digital Sky Survey, measuring the spectroscopic redshift of every galaxy is not feasible. On the other hand, galaxy colors (i.e. the ratio of fluxes -- or difference of magnitudes -- in different bandpass filters used for imaging) tend to correlate well with redshift. This is due to the fact that most galaxies can be classified into a suprisingly small set of spectral types.

As we observe galaxies further away, their spectra are redshifted to longer wavelengths relative to the bandpass filters of the imaging camera. As a result, the ratio of flux in each filter changes with redshift. By reversing this effect, one can obtain an estimate on the redshift of a galaxy just by looking at the measured flux ratios in the various filters of the photometric system. There are several methods to this.

The theoretically motivated method uses spectrum templates to fit galaxy colors. In this process, we start with a template set which covers most galaxy spectral types. We try each template and gradually increase its redshift in small steps. At each small redshift step we calculate the _synthetic magnitude_ of the template in through each filter curve's transmission function. This way the best fit redshift and galaxy type can be determined and the method also allows for finding the galaxy's spectral type.

Empirical methods, on the other hand, start with a _training set_ instead of theoretical template spectra. A training set consits of galaxies with both known color indices and spectroscopic redshifts. Then we apply various types of machine learning algorithms (polynomial fitting, local linear regression, kNN, random forest or even deep learning) to learn correlations from the training set and apply it to the large unknown ensemble of photometry-only galaxies. This method relies heavily on the quality of the training set. The training set should cover the entire redshift and color range of the photometric sample, which condition is rarely satisfied as the photometric sample is deeper (i.e. contains fainter galaxies). Empirical methods can be used for extrapolation but the validity of the extrapolated redshifts is hard to verify without additional spectroscopic follow-up observations.

* Link to Csabai et al. (2002) paper: http://adsabs.harvard.edu/abs/2000AJ....119...69C
* Link to the Beck et al. (2016) paper: http://adsabs.harvard.edu/abs/2016MNRAS.460.1371B
* Link to Beck et al. (2016) web site: http://www.vo.elte.hu/papers/2016/photoz/

## Tasks

### 1. Data aquisition

Register to SDSS SkyServer and collect the necessary data from the SDSS DR7 main galaxy sample. Preferably use the database to compute the absolute magnitudes. You will need the `PhotoObj` table to get the magnitudes `modelMag_*` and foreground extinction values `extinction_*`. Filter the data set to contain galaxies only. The best-suited property to do the filtering is `probPSF` which gives the probability of an object being a point source instead of a resolved source. A low-redshift spectroscopic training set can be constructed by joining on the `SpecObj` table which contains the redshift in column `z`. Joins have to be made on the `PhotoObj.objID = SpecObj.bestObjID` foreign key. For a higher redshift training set, download the data file of Beck et al. (2016).

### 2. Empirical methods

After evaluating the acquired data set, split the training set in half and try several machine learning methods from scikit learn to estimate the photometric redshift of the training set. Split the training set in half for testing purposes. Try the kNN, SVM and random forest estimators. Compare the methods by drawing appropriate plots and evaluate the behavior of errors.

### 3. Local linear regression method

Reproduce the empirical photo-z method and results of Beck et al using their local linear regression method.

### 4. Template-based photo-z

Implement a template-based photo-z algorithm. You can use the galaxy spectrum templates or composite spectra with high signal-to-noise ratio from the links below. After fitting the spectral energy distribution, also compute the K-correction for each galaxy. 

Template spectra can be found in the database referred in [Dobos et al. MNRAS 420, no. 2 (2012): 1217-1238.](https://arxiv.org/abs/1111.1215).  Or you can use empirical templates from https://github.com/gbrammer/eazy-photoz/tree/master/templates/CWW%2BKIN (or other spectra from that site).

SDSS filter profile curves can be downloaded from [here](http://voservices.net/filter/filterlist.aspx?mode=keyword&keyword=sdss) (click "Details" on the right, and then "Get ASCII" )
