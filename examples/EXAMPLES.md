# Examples
The examples in the folders are explained with the command used to generate the plots.

## [gaussian-distribution](examples/gaussian-distribution)
Convolute each point in [some_data.dat](examples/gaussian-distribution/some_data.dat) with a Gaussian distribution
with a FWHM of 0.15.
General `gnuplot` commands are given in [gnuplot_convolution.global.gpi](gnuplot_convolution.global.gpi),
while commands specific to [some_data.dat](examples/gaussian-distribution/some_data.dat) 
are  defined in [some_data.local.gpi](examples/gaussian-distribution/some_data.local.gpi)
To generate 
[some_data.gpi](examples/gaussian-distribution/some_data.gpi) and 
[some_data.pdf](examples/gaussian-distribution/some_data.pdf)
execute
```
gnuplot_convolution some_data.dat -g 0.15
```

## [multiple-inputs](examples/multiple-inputs)
Convolute all column pairs, i.e. 1/2, 3/4 and 5/6, with a Cauchy distribution with a FWHM of 0.2 from 
[first_data.dat](examples/multiple-inputs/first_data.dat),
but only column 2 against 3 from [second_data.dat](examples/multiple-inputs/second_data.dat).
```
gnuplot_convolution first_data.dat second_data.dat -p 2 3 -c 0.2 
```
Again, general `gnuplot` commands are given in 
[gnuplot_convolution.global.gpi](gnuplot_convolution.global.gpi).
The commands specific to this plot are defined in the `first_file_name.local.gpi` 
unless the basename is altered with `--output-base`.
