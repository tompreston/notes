# Rsync
Here are some typical rsync flags.

Copy the contents of foo dir into bar (trailing slash):

    rsync -a --progress remote:foo/ bar

Copy the foo dir into bar (trailing slash):

    rsync -a --progress remote:foo bar

Copy the files/directories in foo dir, matching the filter file into bar:

    rsync -a --progress --filter="match filter-file.txt" remote:foo/ bar

The filter file looks like this. Each dir level is matched against the filters,
so we have to include all sub-directories separately, and also exclude
directories before including recursively (see ts007/tools/output).  Default is
to include all, so we have to exclude all right at the end.

    + conferences
    + README.md
    + slides
    + slides/**
    + standup
    + ts007
    + ts007/debug
    + ts007/debug/**
    + ts007/tools
    - ts007/tools/output
    + ts007/tools/**
    - *

More info:

    man rsync /INCLUDE/EXCLUDE PATTERN RULES
