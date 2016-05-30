# singularity

Scripts for singularity transcoding VM.
More: <http://brontosaurusrex.github.io/singularity/>

## Probably working scripts at this point

### production
- toX264crf (and required toAAC, hasVideo, hasAudio, mxfmixdown and such modules)  
- toDV  
- toPRORES  
- srt2video

### experiments
- toVP9 (needs testing and finding some nice vp9 defaults, so far it looks worse & is slower than x.264 everytime) <http://wiki.webmproject.org/ffmpeg/vp9-encoding-guide>  
- toHEVC (testing x.265)

## changelog

- unique ouput naming for video scripts  
- Lossy audio encoders should now call r128corectionPlus6 (adding +6 dB to calculation), this are all formats meant for web mostly.  
- Broadcast formats like toPRORES will not get any r128 corrections at this point, except formats that are meant for push, like mxf.  

## interesting usage examples

    input=file.mov
    toDV "$input" && toX264crf "$input"
    # will encode the file to DV and h.264
    # toDV "$input" & toX264crf "$input" # should work as well.
    
## fails

toVORBIS fails when run in BG.  

## system notes

Get Thunar some thumbnail

    sudo pacman -S tumbler ffmpegthumbnailer # to get thumbs in thunar
    
Thunar custom actions

    urxvt -e bash -c 'mediainfo %f && (read -n1 -r -p "Any key to quit...")'
