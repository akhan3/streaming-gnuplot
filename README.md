# Realtime stream plotting with gnuplot

## Requirements
- gnuplot
- Perl
- stdbuf

## Demo
For a demo, use the following snippets.
```
$ ./sine_cosine.pl | ./driveGnuPlots.pl 2 50 500 "Sine" "Cosine"
$ ./sine.pl | ./driveGnuPlots.pl 1 50 "Sine"
```

<a href="https://asciinema.org/a/341114"><img src="https://asciinema.org/a/341114.png" width="500px"/></a>


## CPU utilization
To plot CPU utilization for the past 60 seconds, use the snippet below.
```
$ vmstat 1 | stdbuf -oL awk '{print "0:" 100-$(NF-2)}' | ./driveGnuPlots.pl 1 60 "CPU"
```

Please note that `stdbuf` is the key here, without which the pipeline won't work as intended.

<a href="https://asciinema.org/a/341132"><img src="https://asciinema.org/a/341132.png" width="500px"/></a>


## Credits
Idea and initial code is taken from https://www.thanassis.space/gnuplotStreaming.html
