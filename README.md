# To run benchmark:

    for r in bare kata runc; do
        for c in 1 64; do
            for f in randread read randwrite write; do
                make remote RESULTS_PATH=kata-vs-crio/$r/ OUTPUT_PATH=kata-vs-crio/parsed/$r/ NUM_CLIENTS=$c FIO_RW=$f;
            done
        done
    done

# To generate results:

    for r in bare kata runc; do
        for c in 1 64; do
            for f in randread read randwrite write; do
                make parse RESULTS_PATH=kata-vs-crio/$r/ OUTPUT_PATH=kata-vs-crio/parsed/$r/ NUM_CLIENTS=$c FIO_RW=$f SKIP_BS=256;
            done
        done
    done
