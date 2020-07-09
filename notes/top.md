# top
Some quick info about top.

Linux loadavg is system load, not just CPU load. See Brendan's article on
[linux-load-averages](http://www.brendangregg.com/blog/2017-08-08/linux-load-averages.html).

You can plot top, with [topplot](https://gitlab.com/eBardie/topplot).

Record 60s of thread activity in batch mode:

    timeout 60 top -H -b > /tmp/top.log

Or just get a single task snapshot:

    top -b -n1

Useful keys:

| key | description |
| --- | --- |
| ?   | view help |
| <,> | Sort column left right, default is %CPU. |
| R   | Reverse sort order, default is reversed obviously (/top/) |
| H   | Toggle Threads/Tasks, you can see this on the second line |
