# FTrace

- http://lwn.net/Articles/365835/
- http://lwn.net/Articles/366796/
- https://lwn.net/Articles/370423/
- https://lwn.net/Articles/324754/

Enable the following kernel configs:

    CONFIG_FUNCTION_TRACER
    CONFIG_DYNAMIC_FTRACE
    CONFIG_FUNCTION_GRAPH_TRACER
    CONFIG_FUNCTION_PROFILER

Move into the debugfs tracing dir (mount debugfs if necessary):

    cd /sys/kernel/debug/tracing/

# function

    # filter all functions beginning with "tegra30"
    echo "tegra30*" > set_ftrace_filter
    cat set_ftrace_filter

    # turn on the function tracer
    echo function > current_tracer
    echo 1 > tracing_on

    # do something to get a trace
    aplay /usr/share/sounds/alsa/Front_Center.wav

    # view the trace
    cat trace
    # tracer: function
    #
    # entries-in-buffer/entries-written: 97/97   #P:4
    #
    #                              _-----=> irqs-off
    #                             / _----=> need-resched
    #                            | / _---=> hardirq/softirq
    #                            || / _--=> preempt-depth
    #                            ||| /     delay
    #           TASK-PID   CPU#  ||||    TIMESTAMP  FUNCTION
    #              | |       |   ||||       |         |
               aplay-5598  [000] ...1   247.811449: tegra30_i2s_startup <-soc_pcm_open
               aplay-5598  [000] d..2   247.811462: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..2   247.811465: tegra30_i2s_volatile_reg <-regmap_volatile
               aplay-5598  [000] d..2   247.811466: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..2   247.811471: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..2   247.811472: tegra30_i2s_volatile_reg <-regmap_volatile
               aplay-5598  [000] d..2   247.811475: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..2   247.811476: tegra30_i2s_volatile_reg <-regmap_volatile
               aplay-5598  [000] d..2   247.811477: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..2   247.811479: tegra30_i2s_volatile_reg <-regmap_volatile
               aplay-5598  [000] d..2   247.811480: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..2   247.811482: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..2   247.811483: tegra30_i2s_volatile_reg <-regmap_volatile
               aplay-5598  [000] d..2   247.811485: tegra30_i2s_wr_rd_reg <-regmap_writeable
               aplay-5598  [000] d..2   247.811487: tegra30_i2s_wr_rd_reg <-_regmap_raw_write
               aplay-5598  [000] d..2   247.811490: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..2   247.811491: tegra30_i2s_volatile_reg <-regmap_volatile
               aplay-5598  [000] ...1   247.811812: tegra30_i2s_hw_params <-soc_dai_hw_params
               aplay-5598  [000] d..2   247.811817: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..2   247.811818: tegra30_i2s_volatile_reg <-regmap_volatile
               aplay-5598  [000] d..2   247.811821: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..2   247.811822: tegra30_i2s_volatile_reg <-regmap_volatile
               aplay-5598  [000] d..2   247.811823: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..2   247.811826: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..2   247.811827: tegra30_i2s_volatile_reg <-regmap_volatile
               aplay-5598  [000] d..2   247.811836: tegra30_i2s_wr_rd_reg <-regmap_writeable
               aplay-5598  [000] d..2   247.811837: tegra30_i2s_wr_rd_reg <-_regmap_raw_write
               aplay-5598  [000] d..2   247.811839: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..2   247.811841: tegra30_i2s_volatile_reg <-regmap_volatile
               aplay-5598  [000] ...1   247.811845: tegra30_ahub_set_cif <-tegra30_i2s_hw_params
               aplay-5598  [000] d..2   247.811847: tegra30_i2s_wr_rd_reg <-regmap_writeable
               aplay-5598  [000] d..2   247.811848: tegra30_i2s_wr_rd_reg <-_regmap_raw_write
               aplay-5598  [000] d..2   247.811850: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..2   247.811851: tegra30_i2s_volatile_reg <-regmap_volatile
               aplay-5598  [000] ...1   247.811855: tegra30_ahub_setup_tx_fifo <-tegra30_i2s_hw_params
               aplay-5598  [000] d..2   247.811858: tegra30_ahub_apbif_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..2   247.811860: tegra30_ahub_apbif_volatile_reg <-regmap_volatile
               aplay-5598  [000] d..2   247.811863: tegra30_ahub_apbif_wr_rd_reg <-regmap_writeable
               aplay-5598  [000] d..2   247.811864: tegra30_ahub_apbif_wr_rd_reg <-_regmap_raw_write
               aplay-5598  [000] d..2   247.811865: tegra30_ahub_apbif_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..2   247.811867: tegra30_ahub_apbif_volatile_reg <-regmap_volatile
               aplay-5598  [000] ...1   247.811869: tegra30_ahub_set_cif <-tegra30_ahub_setup_tx_fifo
               aplay-5598  [000] d..2   247.811871: tegra30_ahub_apbif_wr_rd_reg <-regmap_writeable
               aplay-5598  [000] d..2   247.811872: tegra30_ahub_apbif_wr_rd_reg <-_regmap_raw_write
               aplay-5598  [000] d..2   247.811874: tegra30_ahub_apbif_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..2   247.811875: tegra30_ahub_apbif_volatile_reg <-regmap_volatile
               aplay-5598  [000] d..2   247.811877: tegra30_i2s_wr_rd_reg <-regmap_writeable
               aplay-5598  [000] d..2   247.811878: tegra30_i2s_wr_rd_reg <-_regmap_raw_write
               aplay-5598  [000] d..2   247.811880: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..2   247.811881: tegra30_i2s_volatile_reg <-regmap_volatile
               aplay-5598  [000] d..3   247.812191: tegra30_i2s_trigger <-soc_pcm_trigger
               aplay-5598  [000] d..3   247.812194: tegra30_ahub_enable_tx_fifo <-tegra30_i2s_trigger
               aplay-5598  [000] d..4   247.812197: tegra30_ahub_apbif_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..4   247.812199: tegra30_ahub_apbif_volatile_reg <-regmap_volatile
               aplay-5598  [000] d..4   247.812201: tegra30_ahub_apbif_wr_rd_reg <-regmap_writeable
               aplay-5598  [000] d..4   247.812203: tegra30_ahub_apbif_wr_rd_reg <-_regmap_raw_write
               aplay-5598  [000] d..4   247.812204: tegra30_ahub_apbif_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..4   247.812206: tegra30_ahub_apbif_volatile_reg <-regmap_volatile
               aplay-5598  [000] d..4   247.812209: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..4   247.812211: tegra30_i2s_volatile_reg <-regmap_volatile
               aplay-5598  [000] d..4   247.812212: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..4   247.812213: tegra30_i2s_volatile_reg <-regmap_volatile
               aplay-5598  [000] d..4   247.812214: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..4   247.812217: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..4   247.812218: tegra30_i2s_volatile_reg <-regmap_volatile
               aplay-5598  [000] d..4   247.812219: tegra30_i2s_wr_rd_reg <-regmap_writeable
               aplay-5598  [000] d..4   247.812221: tegra30_i2s_wr_rd_reg <-_regmap_raw_write
               aplay-5598  [000] d..4   247.812222: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [000] d..4   247.812223: tegra30_i2s_volatile_reg <-regmap_volatile
               aplay-5598  [002] d..3   249.252237: tegra30_i2s_trigger <-soc_pcm_trigger
               aplay-5598  [002] d..3   249.252251: tegra30_ahub_disable_tx_fifo <-tegra30_i2s_trigger
               aplay-5598  [002] d..4   249.252258: tegra30_ahub_apbif_wr_rd_reg <-regmap_readable
               aplay-5598  [002] d..4   249.252260: tegra30_ahub_apbif_volatile_reg <-regmap_volatile
               aplay-5598  [002] d..4   249.252265: tegra30_ahub_apbif_wr_rd_reg <-regmap_writeable
               aplay-5598  [002] d..4   249.252269: tegra30_ahub_apbif_wr_rd_reg <-_regmap_raw_write
               aplay-5598  [002] d..4   249.252271: tegra30_ahub_apbif_wr_rd_reg <-regmap_readable
               aplay-5598  [002] d..4   249.252272: tegra30_ahub_apbif_volatile_reg <-regmap_volatile
               aplay-5598  [002] d..4   249.252279: tegra30_ahub_apbif_wr_rd_reg <-regmap_readable
               aplay-5598  [002] d..4   249.252280: tegra30_ahub_apbif_volatile_reg <-regmap_volatile
               aplay-5598  [002] d..4   249.252281: tegra30_ahub_apbif_wr_rd_reg <-regmap_readable
               aplay-5598  [002] d..4   249.252286: tegra30_ahub_apbif_wr_rd_reg <-regmap_readable
               aplay-5598  [002] d..4   249.252287: tegra30_ahub_apbif_volatile_reg <-regmap_volatile
               aplay-5598  [002] d..4   249.252289: tegra30_ahub_apbif_wr_rd_reg <-regmap_writeable
               aplay-5598  [002] d..4   249.252290: tegra30_ahub_apbif_wr_rd_reg <-_regmap_raw_write
               aplay-5598  [002] d..4   249.252292: tegra30_ahub_apbif_wr_rd_reg <-regmap_readable
               aplay-5598  [002] d..4   249.252293: tegra30_ahub_apbif_volatile_reg <-regmap_volatile
               aplay-5598  [002] d..4   249.252298: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [002] d..4   249.252300: tegra30_i2s_volatile_reg <-regmap_volatile
               aplay-5598  [002] d..4   249.252302: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [002] d..4   249.252303: tegra30_i2s_volatile_reg <-regmap_volatile
               aplay-5598  [002] d..4   249.252304: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [002] d..4   249.252306: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [002] d..4   249.252308: tegra30_i2s_volatile_reg <-regmap_volatile
               aplay-5598  [002] d..4   249.252309: tegra30_i2s_wr_rd_reg <-regmap_writeable
               aplay-5598  [002] d..4   249.252310: tegra30_i2s_wr_rd_reg <-_regmap_raw_write
               aplay-5598  [002] d..4   249.252312: tegra30_i2s_wr_rd_reg <-regmap_readable
               aplay-5598  [002] d..4   249.252313: tegra30_i2s_volatile_reg <-regmap_volatile

You can even get stack traces (only when current_tracer == function)

    echo 0 > tracing_on # reset tracer
    echo function > current_tracer
    echo 1 > options/func_stack_trace
    echo tegra30_i2s_trigger > set_ftrace_filter # reduce filter to 1 func
    echo 1 > tracing_on
    aplay /usr/share/sounds/alsa/Front_Center.wav
    cat trace
    # tracer: function
    #
    # entries-in-buffer/entries-written: 4/4   #P:4
    #
    #                              _-----=> irqs-off
    #                             / _----=> need-resched
    #                            | / _---=> hardirq/softirq
    #                            || / _--=> preempt-depth
    #                            ||| /     delay
    #           TASK-PID   CPU#  ||||    TIMESTAMP  FUNCTION
    #              | |       |   ||||       |         |
               aplay-14766 [003] d..3   790.704911: tegra30_i2s_trigger <-soc_pcm_trigger
               aplay-14766 [003] d..3   790.704959: <stack trace>
     => tegra30_i2s_trigger
     => soc_pcm_trigger
     => snd_pcm_do_start
     => snd_pcm_action_single
     => snd_pcm_action
     => snd_pcm_common_ioctl1
     => snd_pcm_playback_ioctl1
     => snd_pcm_playback_ioctl
     => do_vfs_ioctl
     => SyS_ioctl
     => ret_fast_syscall
               aplay-14766 [001] d..3   792.139335: tegra30_i2s_trigger <-soc_pcm_trigger
               aplay-14766 [001] d..3   792.139400: <stack trace>
     => tegra30_i2s_trigger
     => soc_pcm_trigger
     => snd_pcm_do_stop
     => snd_pcm_action_single
     => snd_pcm_action
     => snd_pcm_drop
     => snd_pcm_release_substream.part.9
     => snd_pcm_release
     => __fput
     => ____fput
     => task_work_run
     => do_work_pending
     => slow_work_pending

# function_graph

    echo function_graph > current_tracer
    aplay /usr/share/sounds/alsa/Front_Center.wav
    cat trace
    # tracer: function_graph
    #
    # CPU  DURATION                  FUNCTION CALLS
    # |     |   |                     |   |   |   |
     3)               |  tegra30_i2s_startup() {
     3)   1.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   1.000 us    |    tegra30_i2s_volatile_reg();
     3)   0.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   1.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   0.000 us    |    tegra30_i2s_volatile_reg();
     3)   0.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   1.000 us    |    tegra30_i2s_volatile_reg();
     3)   0.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   1.000 us    |    tegra30_i2s_volatile_reg();
     3)   1.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   0.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   0.000 us    |    tegra30_i2s_volatile_reg();
     3)   1.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   0.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   1.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   1.000 us    |    tegra30_i2s_volatile_reg();
     3) + 82.000 us   |  }
     3)               |  tegra30_i2s_hw_params() {
     3)   1.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   1.000 us    |    tegra30_i2s_volatile_reg();
     3)   1.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   0.000 us    |    tegra30_i2s_volatile_reg();
     3)   1.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   0.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   0.000 us    |    tegra30_i2s_volatile_reg();
     3)   0.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   1.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   0.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   1.000 us    |    tegra30_i2s_volatile_reg();
     3)               |    tegra30_ahub_set_cif() {
     3)   1.000 us    |      tegra30_i2s_wr_rd_reg();
     3)   1.000 us    |      tegra30_i2s_wr_rd_reg();
     3)   0.000 us    |      tegra30_i2s_wr_rd_reg();
     3)   1.000 us    |      tegra30_i2s_volatile_reg();
     3) + 16.000 us   |    }
     3)               |    tegra30_ahub_setup_tx_fifo() {
     3)   1.000 us    |      tegra30_ahub_apbif_wr_rd_reg();
     3)   1.000 us    |      tegra30_ahub_apbif_volatile_reg();
     3)   1.000 us    |      tegra30_ahub_apbif_wr_rd_reg();
     3)   0.000 us    |      tegra30_ahub_apbif_wr_rd_reg();
     3)   1.000 us    |      tegra30_ahub_apbif_wr_rd_reg();
     3)   0.000 us    |      tegra30_ahub_apbif_volatile_reg();
     3)               |      tegra30_ahub_set_cif() {
     3)   1.000 us    |        tegra30_ahub_apbif_wr_rd_reg();
     3)   0.000 us    |        tegra30_ahub_apbif_wr_rd_reg();
     3)   1.000 us    |        tegra30_ahub_apbif_wr_rd_reg();
     3)   0.000 us    |        tegra30_ahub_apbif_volatile_reg();
     3) + 16.000 us   |      }
     3) + 46.000 us   |    }
     3)   1.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   0.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   1.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   0.000 us    |    tegra30_i2s_volatile_reg();
     3) ! 146.000 us  |  }
     3)               |  tegra30_i2s_trigger() {
     3)               |    tegra30_ahub_enable_tx_fifo() {
     3)   1.000 us    |      tegra30_ahub_apbif_wr_rd_reg();
     3)   1.000 us    |      tegra30_ahub_apbif_volatile_reg();
     3)   1.000 us    |      tegra30_ahub_apbif_wr_rd_reg();
     3)   0.000 us    |      tegra30_ahub_apbif_wr_rd_reg();
     3)   0.000 us    |      tegra30_ahub_apbif_wr_rd_reg();
     3)   1.000 us    |      tegra30_ahub_apbif_volatile_reg();
     3) + 34.000 us   |    }
     3)   0.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   1.000 us    |    tegra30_i2s_volatile_reg();
     3)   0.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   1.000 us    |    tegra30_i2s_volatile_reg();
     3)   1.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   0.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   0.000 us    |    tegra30_i2s_volatile_reg();
     3)   0.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   1.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   0.000 us    |    tegra30_i2s_wr_rd_reg();
     3)   1.000 us    |    tegra30_i2s_volatile_reg();
     3) + 89.000 us   |  }
     2)               |  tegra30_i2s_trigger() {
     2)               |    tegra30_ahub_disable_tx_fifo() {
     2)   1.000 us    |      tegra30_ahub_apbif_wr_rd_reg();
     2)   1.000 us    |      tegra30_ahub_apbif_volatile_reg();
     2)   1.000 us    |      tegra30_ahub_apbif_wr_rd_reg();
     2)   1.000 us    |      tegra30_ahub_apbif_wr_rd_reg();
     2)   1.000 us    |      tegra30_ahub_apbif_wr_rd_reg();
     2)   0.000 us    |      tegra30_ahub_apbif_volatile_reg();
     2)   0.000 us    |      tegra30_ahub_apbif_wr_rd_reg();
     2)   1.000 us    |      tegra30_ahub_apbif_volatile_reg();
     2)   0.000 us    |      tegra30_ahub_apbif_wr_rd_reg();
     2)   0.000 us    |      tegra30_ahub_apbif_wr_rd_reg();
     2)   1.000 us    |      tegra30_ahub_apbif_volatile_reg();
     2)   0.000 us    |      tegra30_ahub_apbif_wr_rd_reg();
     2)   1.000 us    |      tegra30_ahub_apbif_wr_rd_reg();
     2)   1.000 us    |      tegra30_ahub_apbif_wr_rd_reg();
     2)   1.000 us    |      tegra30_ahub_apbif_volatile_reg();
     2) + 75.000 us   |    }
     2)   1.000 us    |    tegra30_i2s_wr_rd_reg();
     2)   1.000 us    |    tegra30_i2s_volatile_reg();
     2)   0.000 us    |    tegra30_i2s_wr_rd_reg();
     2)   1.000 us    |    tegra30_i2s_volatile_reg();
     2)   0.000 us    |    tegra30_i2s_wr_rd_reg();
     2)   0.000 us    |    tegra30_i2s_wr_rd_reg();
     2)   1.000 us    |    tegra30_i2s_volatile_reg();
     2)   0.000 us    |    tegra30_i2s_wr_rd_reg();
     2)   1.000 us    |    tegra30_i2s_wr_rd_reg();
     2)   0.000 us    |    tegra30_i2s_wr_rd_reg();
     2)   0.000 us    |    tegra30_i2s_volatile_reg();
     2) ! 125.000 us  |  }


# function profiling

    echo nop > current_tracer
    echo 1 > function_profile_enabled
    echo "tegra30*" > set_ftrace_filter
    aplay /usr/share/sounds/alsa/Front_Center.wav
    cat trace_stat/function{0,1,2,3} # profiling for each cpu
      Function                               Hit    Time            Avg             s^2
      --------                               ---    ----            ---             ---
      Function                               Hit    Time            Avg             s^2
      --------                               ---    ----            ---             ---
      tegra30_i2s_trigger                      1    68.000 us       68.000 us       0.000 us
      tegra30_ahub_disable_tx_fifo             1    44.000 us       44.000 us       0.000 us
      tegra30_ahub_apbif_wr_rd_reg            10    5.000 us        0.500 us        0.277 us
      tegra30_i2s_wr_rd_reg                    7    4.000 us        0.571 us        0.285 us
      tegra30_ahub_apbif_volatile_re           5    4.000 us        0.800 us        0.200 us
      tegra30_i2s_volatile_reg                 4    2.000 us        0.500 us        0.333 us
      Function                               Hit    Time            Avg             s^2
      --------                               ---    ----            ---             ---
      tegra30_i2s_trigger                      1    31.000 us       31.000 us       0.000 us
      Function                               Hit    Time            Avg             s^2
      --------                               ---    ----            ---             ---
      tegra30_i2s_hw_params                    1    75.000 us       75.000 us       0.000 us
      tegra30_i2s_startup                      1    48.000 us       48.000 us       0.000 us
      tegra30_i2s_trigger                      2    48.000 us       24.000 us       242.000 us
      tegra30_ahub_setup_tx_fifo               1    25.000 us       25.000 us       0.000 us
      tegra30_i2s_wr_rd_reg                   30    18.000 us       0.600 us        0.248 us
      tegra30_ahub_set_cif                     2    15.000 us       7.500 us        0.500 us
      tegra30_ahub_enable_tx_fifo              1    14.000 us       14.000 us       0.000 us
      tegra30_i2s_volatile_reg                16    8.000 us        0.500 us        0.266 us
      tegra30_ahub_apbif_volatile_re           5    5.000 us        1.000 us        0.500 us
      tegra30_ahub_apbif_wr_rd_reg            11    5.000 us        0.454 us        0.272 us

Run with higher level functions to get fine grained performance metrics.

# Function graph tracer

Ed likes this one best :p

Enable with:

    ./scripts/config -e CONFIG_FUNCTION_GRAPH_TRACER

    echo function_graph > current_tracer

# Simple print debugging using Ftrace

Even if you don't use the function tracing features of Ftrace, you can print
messages to the Ftrace ringbuffer manually. This can be useful for annotating
things happening within a trace, or if you need to dump more messages than you
can do to the console.

1. Enable ftrace (`./scripts/config -e CONFIG_FTRACE; ./scripts/config -e CONFIG_DYNAMIC_FTRACE`)
2. Print to the ftrace ring buffer with `ftrace_printk()` like a normal printk
3. `cat /sys/kernel/debug/tracing/trace` to view the messages

