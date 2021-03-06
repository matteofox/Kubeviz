Acknowledgements:

If you use KUBEVIZ in your work please add the following sentence in the ackowledgement section of any resulting publication:

This work made use of the KUBEVIZ software which is publicly available at https://github.com/matteofox/kubeviz/.
The developement of the KUBEVIZ code code was supported by the Deutsche Forschungsgemeinschaft via Project IDs: 
WI3871/1-1 and WI3871/1-2

And please cite Fossati et al. (2016) http://adsabs.harvard.edu/abs/2016MNRAS.455.2028F.

*****************

Setting up kubeviz (V2.0)

1. Setup appropriate directory structure to store kubeviz versions
   outside IDL_PATH 

   mkdir kubeviz

2. Unpack the gzipped tarfile in the directory you have created:

   cd kubeviz
   tar xvfz kubeviz_v2.0.tar.gz

3. This creates a subdirectory with the specific version number 
   e.g. kubeviz/v2.0 Now link the current version inside IDL_PATH (assumed
   IDL root directory $IDL_ROOT):

   ln -s kubeviz/v2.0 $IDL_ROOT/kubeviz_current
   
   Make sure your IDL_PATH runs recusrsively into the subdirectories 
   (addons/ must be in the IDL_PATH).
   
3. Run kubeviz!

   idl
   > kubeviz, 'cube.fits'

4. Documentation
   
   The doc/ directory of the package includes an instruction file
   and a detailed changelog. We suggest you to have a quick look 
   at the instructions.txt file before using the code. This describes
   the calling sequence and the features of the interactive environment.
   
   From the IDL prompt run:
   > doc_library, 'kubeviz'
   to see the header of the code and the available keywords.

   In the GUI, select 
      'help' -> 'Instructions' 
      'help' -> 'What's new' 
   to see the documentation.   
   

!! IMPORTANT !!
  
   Kubeviz requires the following external libraries:
   * Astrolib Library (updated after 2012, or late 2014 if you load MUSE cubes)
         http://idlastro.gsfc.nasa.gov/contents.html
   * Some routines in the astrolib make use of programs in the Coyote Library. 
     Although they have recently bundled into the astrolib package it is 
     recommended to have a full and up-to-date  installation of the Coyote 
     library which must be downloaded separately.
   * Mpfit suite of code (V1.70 or greater)
         http://cow.physics.wisc.edu/~craigm/idl/fitting.html

   If kubeviz does not work properly and stops when calling one of those 
   third-party libraries, the first thing to do is to update the library. 
   Then restart IDL and try again.

(BASIC) TROUBLESHOOTING

1) If you see this message:
    
    [WARNING] ##       This is a 32 bit IDL version.        ##
    [WARNING] ##   Some features might now work correctly!  ##
   
   There is no reason to worry unless you are trying to load a very large 
   datacube. Almost certainly MUSE datacubes require a 64bit IDL version 
   for the load to be successful.

2) If you see errors like:
      
      % Error occurred at: VALID_NUM   line 71     
      % AIRTOVAC: Incorrect number of arguments.
   
   It means you have not updated the Astrolib library since 2012. 
   It is important to keep Astrolib updated frequently as bugs 
   are fixed and the library is gradually being converted to handle 
   64bit variables whenever possible. 

3) If you get an error when you try to load data from an instrument 
   which is not in the list of supported instrument please report it 
   to mfossati at mpe.mpg.de. We will try to solve the issue.
