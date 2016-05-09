# singularity

Scripts for singularity transcoding VM.
More: <http://brontosaurusrex.github.io/singularity/>

## Probably working scripts at this point

toX264crf (and required toAAC, hasVideo, hasAudio, mxfmixdown and such modules)  
toDV  
toPRORES  
toVP9 (needs testing and finding some nice vp9 defaults)  

## changelog

unique ouput naming for video scripts  
Lossy audio encoders should now call r128corectionPlus6 (adding +6 dB to calculation), this are all formats meant for web mostly.  
Broadcast formats like toPRORES will not get any r128 corrections at this point, except formats that are meant for push, like mxf.  

## interesting usage examples

    input=file.mov
    toDV "$input" && toX264crf "$input"
    # will encode the file to DV and h.264
    # toDV "$input" & toX264crf "$input" # should work as well.
    
## fails

toVORBIS fails when run in BG.  

## system notes

    sudo pacman -S tumbler ffmpegthumbnailer # to get thumbs in thunar
    
Thunar custom actions

    urxvt -e bash -c 'mediainfo %f && (read -n1 -r -p "Any key to quit...")'
