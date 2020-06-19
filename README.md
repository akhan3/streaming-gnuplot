# Realtime stream plotting with gnuplot

For a demo, use the following snippets.
```
$ ./sine_cosine.pl | ./driveGnuPlots.pl 2 50 500 "Sine" "Cosine"
$ ./sine.pl | ./driveGnuPlots.pl 1 50 "Sine"
```

To plot CPU utilization, use the snippet below.
```
$ vmstat 1 | stdbuf -oL awk '{print "0:" 100-$(NF-2)}' | ./driveGnuPlots.pl 1 60 "CPU"

```

Please note that `stdbuf` is the key here, without which the pipeline won't work as intended.


## Credits
Idea and initial code is taken from https://www.thanassis.space/gnuplotStreaming.html
