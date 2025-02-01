# CZII - 3D Object Identification 
Dataset Description
This competition is focused on identifying points corresponding to particle centers in 3D tomograms. For testing you will have a list of 3D arrays to process named "experiments", and you will need to submit a CSV with particle locations of 5 particle types in all experiments.

The data contains 6 particle types with different difficulty levels of prediction.

apo-ferritin (easy)
beta-amylase (impossible, not scored)
beta-galactosidase (hard)
ribosome (easy)
thyroglobulin (hard)
virus-like-particle (easy)
Note that beta-amylase is not scored because it is considered to be too difficult for accurate evaluation. It is included in the data, but whether or not it is predicted has no bearing on the score.

File Information
train/
static/ExperimentRuns/{experiment}/VoxelSpacing10.000/
denoised.zarr/ - zarr files of experiment containing tomograph data
{3 other data filtered options, which are not included in test}
overlay/ExperimentRuns/{experiment}/Picks/
{particle_type}.json - ground truth files containing coordinates of particles
test/
static/ExperimentRuns/{experiment}/VoxelSpacing10.000/
denoised.zarr/ - zarr files of experiment containing tomograph data
sample_submission.csv - a submission file in the correct format
The test dataset on this page is example data copied over from the training dataset. The rerun test dataset contains ~500 tomographs.

Tomograms
The tomograms are 3D arrays, and are provided as multiscale 3D OME-NGFF Zarr arrays. Tomograms can be opened with the zarr, ome-zarr, and copick libraries.

In the training data 4 filtered versions of the tomograms are provided. (Only the denoised option is included in the test data.)

denoised (this is the only tomogram type included in test)
wbp (weighted back projection)
ctfdeconvolved
isonetcorrected
These zarrs can be found in the competition directory, and details about their methods can be found in the preprint mentioned in the pinned welcome post. Note that these are multiscale zarr arrays, and 0 corresponds to the highest resolution. You can use copick to traverse the zarrs and maintain associations with labels, see the pinned notebooks.

Particle locations
Particle locations are stored in json files according to the copick specification. You can use copick to read from the json files and perform utility functions like converting points into segmentation masks, see the pinned notebooks.

If you intend to use copick to get tomograms, points, and labels, then see the example notebooks which provide examples for access to tomograms and making valid predictions of particle locations.


