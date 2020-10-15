# Perf Performance Monitoring
- Using Perf on ARM Platforms, Linaro
  https://s3.amazonaws.com/connect.linaro.org/yvr18/presentations/yvr18-416.pdf
  https://s3.amazonaws.com/connect.linaro.org/yvr18/videos/yvr18-416.mp4

# Basic usage
See available counters:

    perf list

Free-run to display counters of ls:

    perf stat ls

Free-run to display counters of gnome-terminal-server over 5 seconds:

    perf stat -p $(pidof gnome-terminal-server) -- sleep 5

# Recording
TODO more notes on this, it's really useful and shows userland behaviour.

Record PID 375 for 10 seconds:

    perf record -F 1000 -p 375 -g -- sleep 10
    perf report -n --stdio > /tmp/trace.txt
