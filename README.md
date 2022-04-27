# VERSE

VERSE is designed for high-performance read summarization for next generation sequencing. VERSE is 50x faster than HTSeq when computing the same gene counts. It introduces a novel, hierarchical assignment scheme, which allows simultaneous quantification of multiple feature types or annotation levels without repeatedly assigning reads. There is also a set of parameters the user can use to fine-tune the assignment logic. VERSE can be readily incorporated into any existing RNA-Seq analysis pipelines.

VERSE supports the following modes of RNA-Seq quantification:
1. Original featureCounts (Default)
2. HTSeq Union (-z 1)
3. HTSeq Intersection-strict (-z 2)
4. HTSeq Intersection-nonempty (-z 3)
5. VERSE Union-strict (-z 4)
6. VERSE Cover-length (-z 5)

Supported Quantification Schemes:

Hierarchical Assign: assign reads to feature types according to their priority.

Independent Assign: assign reads to feature types independently in a single run.

## Installation 

You can type `make` to see instructions.
For Linux OS:

```
make -f Makefile.Linux
```

For Mac OS, use command:

```
make -f Makefile.MacOS
```

## Usage

Please run `./verse` to see the details.

A sample command:

```
./verse -a testdata/test.gtf -t 'exon' -g gene_id -z 3 -s 1 -o testdata/intersection_nonempty.stranded.paired testdata/PE.sam
```

A sample hierarchical assign command:

```
./verse -a testdata/test.gtf -t 'exon;intron;xine' -g gene_id -z 3 -o testdata/intersection_nonempty.unstranded.paired.hierarchical testdata/PE.sam
```

VERSE is developed based on the framework of featureCounts(SUBREAD), which is written by Drs Yang Liao and Wei Shi.
Dr. Stephen Fisher and Professor Junhyong Kim supervised and Qin Zhu developed VERSE.
