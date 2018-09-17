# R
R is an integrated suite of software facilities for data manipulation.

https://cran.r-project.org/doc/manuals/r-release/R-intro.html#A-sample-session

# Build packages
Great link:
- http://kbroman.org/pkg_primer/pages/build.html

    git clone https://github.com/ThinkR-open/collage.git
    R CMD build collage

# Plotting simple differentials

    # simple R script for plotting differential of tidy data
    # usage: Rscript process.R out.dat
    args <- commandArgs(TRUE)

    logfile <- args[1]
    print(paste("log file is", logfile))

    log <- read.table(logfile, header=FALSE)
    # set colnames if necessary, otherwise we can refer to values with V1, V2...
    colnames(log) <- c("timestamp", "counter", "counter2")

    # add differential (+1 empty row at start)
    log$dcounter <- c(NA, diff(log$counter))

    # plot to pdf
    pdf(file="plot.pdf")

    # wrap with X11() and locator(1) to persist
    #X11()
    with(log, plot(timestamp, dcounter, type="l"))
    #locator(1)
