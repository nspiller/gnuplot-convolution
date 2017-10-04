# gnuplot-convolution

This `bash` script creates convolutions (e.g. Gaussian or Cauchy) of impulse spectra
with `gnuplot`.

## Setup
Download repository as a Zip-archive or use:
```
git clone https://github.com/nspiller/gnuplot-convolution
```
Add the folder to your path variable and make [gnuplot_convolution](gnuplot_convolution) 
executable with `chmod u+x gnuplot_convolution`.

## Minimum working example
The input file and the desired distribution
with the full width at half medium (FWHM) has to be supplied, e.g.:
```
gnuplot_convolution inputfile.dat -c 0.2
```
In the input file, the data needs to be stored in whitespace-separated columns, since `awk` is used to process the files.
The columns headers are used to generate the name in the key of the plot.


## Default behaviour
By default column pairs are plotted for each input file,
so column 1 is plotted against column 2, 3 against 4 etc.
The column pair can be specified by giving the `--column-pair` argument **directly
after** the input file, e.g: 
```
gnuplot_convolution inputfile.dat -p 3 1 inputfile.dat -p 2 7 
```

Only the convolutions are plotted. The impuls spectrum can be plotted
with `--plot-impulses`

The suffix `.dat` is automatically stripped from the input file
name and the basename is used to write `inputfile.gpi` and `inputfile.pdf`.
The basename can be changed with `--output-base`.

Some default values can be set directly in [gnuplot_convolution](gnuplot_convolution)  
in the "Default variable declaration" section.

## Global and local `gnuplot` commands
To assure a uniform layout of the plots, gnuplot settings can be 
specified on two levels of hierarchy. General settings (e.g. appearance) can be 
stored in [gnuplot_convolution.global.gpi](gnuplot_convolution.global.gpi). 
Settings specific to each plot (e.g. minimum and maximum of the axis) 
can be stored for each `inputfile.dat` in that folder
in an individual file named `inputfile.local.gpi`.


## More features
### Merge several datafiles in one plot
Multiple input files are supported:
```
gnuplot_convolution inputfile_1.dat -p 1 2 inputfile_2.dat -p 4 7 inputfile_3.dat
```

### Reusing the `gnuplot` code 
The execution of `gnuplot` can be suppressed with `--plot-nothing`. This can be 
useful if the code block is to be used in another programme.

## Examples
Look in [examples](examples/) for some use cases.
