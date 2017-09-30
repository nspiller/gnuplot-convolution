This programme creates convolutions (e.g. Gaussian or Cauchy) of impulse spectra



>>> Minimum working example

For the minimum working example an input file and the desired distribution
with the full width at half medium (FWHM) has to be supplied, e.g.:
	gnuplot_convolution inputfile.dat -c 0.2
In the input file, the data needs to be stored in whitespace-separated columns.
The columns headers are used to generate the name in the key of the plot.


>>> Default behaviour

In the input file pairs of columns are used for the convolutions,
so column 1 is plotted against column 2, 3 against 4 etc.
The column pair can be specified by giving the --column-pair argument directly
after the input file, e.g: 
	gnuplot_convolution inputfile.dat -p 3 1 inputfile.dat -p 2 7 

Only the convolutions are plotted. The impulss spectrum can be plotted
with --plot-impulses

The suffix ".dat" is automatically stripped from the input file
name and the basename is used to write inputfile.gpi and inputfile.pdf.
This can be changed with --output-base  

Some default values can be altered directly in the gnuplot_convolution file 
in the "Default variable declaration" section.

>>> global and local gnuplot settings

To assure a uniform layout of the resulting graphs, gnuplot settings can be 
specified on two levels of hierarchy. General settings (e.g. appearence) can be 
stored in the gnuplot_convolution.global.gpi in the folder of the 
gnuplot_convolution executable. Settings specific to each plot (e.g. minimum
and maximum of the axis) can be stored for each inputfile.dat in that folder
in inputfile.local.gpi.


>>> More features

Multiple input files are supported:
	gnuplot_convolution inputfile_1.dat -p 1 2 inputfile_2.dat -p 4 7 inputfile_3.dat

The excecution of gnuplot can be surpressed with --plot-nothing, wich can be 
useful if the gnuplot code block is to be used in another programme.


>>> Examples
In the example directory examples are given for some cases

1) gaussian_distribution
With both some_data.dat and some_data.local.gpi present, execute
	gnuplot_convolution some_data.dat -g 0.15

2) multiple_inputs
Convolute all column pairs with a Cauchy distribution from first_data.dat 
and only 2 against 3 from second_data.dat:
	gnuplot_convolution first_data.dat second_data.dat -p 2 3 -c 0.2	

