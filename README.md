# singularity

Scripts for singularity transcoding VM.
More: <http://brontosaurusrex.github.io/singularity/>

## Probably working scripts at this point

toX264crf (and required toAAC, hasVideo, hasAudio, mxfmixdown and such modules)  
toDV
toPRORES

## changelog

unique ouput naming for video scripts

## interesting usage examples

    input=file.mov
    toDV "$input" && toX264crf "$input"
    # will encode the file to DV and h.264
    # toDV "$input" & toX264crf "$input" # should work as well.
    
## fails

toVORBIS fails when run in BG.
