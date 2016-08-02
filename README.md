# singularity

Scripts for singularity transcoding VM.  
For What, Why, How you could read: <http://brontosaurusrex.github.io/singularity/>

## Probably working scripts at this point

### production
- toX264crf (and required toAAC, hasVideo, hasAudio, mxfmixdown and such modules)  
- toDV  
- toPRORES  
- srt2video
- toMXFpush (xdcam 8bpc 4:2:2 mpeg2 with separated mono tracks, assumes stereo single channel input)
- r128 (r128 info and graph, will also work with mxf files with separated audio channels)

    MXF detected
    /home/ticho/output/osmici.mxf
    size=    3234kB time=00:00:23.00 bitrate=1152.0kbits/s speed=57.6x    
    pcm_s24le ([1][0][0][0] / 0x0001), 48000 Hz, stereo, s32 (24 bit), 2304 kb/s - 23 s 0 ms
    -4.6		dB max volume
    -23.0		LUFS Integrated loudness (I)
    5.2		LU Loudness Range (LRA)
    0 		dB correction, NO correction needed, smaller than 1 dB
    
                                                                                                                                                                                                          
     -10 +-+                                   +                                     +                                    +                                     +                                   +-+   
         +                                     +                                     +                                    +                                     +                                     +   
                                                                                                                                                                                                          
                                                                                                                                                                                                          
     -15 +-+     *                                                                                                                                                                                  +-+   
                * *                                                                                                                 **                                                                    
               *  *                                                                                                                 * *                                                                   
              *    *                                                      *                                                        *  *                                                                   
     -20 +-+ *     *  ***                                                * *               **  ****                                *   *            *                                               +-+   
             *     * *  *             *                                  *  **        ** **  * *   **                              *   *           * *                                                    
             *      **  *    **      **    **                           *     *      *  *     *      **                           *     *  **     *   *                                                   
             *      *    *   * *    *  *  *  *             ***   **     *      *     *                 *                     **   *     * *  **  *     **            ****                                 
     -25 +-+ *           *  *  *    *  ***    **          *   ***  *    *       *   *                  *        ***         *  *  *      *     **        **          *   **                         +-+   
             *           ** *   *  *            ******* **          *  *         *  *                   **    **   ***     *    **                         **        *     *                              
             *             *    *  *                   *             ***         *  *                     ** *        **** *     *                           *      *       *                             
             *                  ***                                               **                        *             *                                   **   **       *   ********                  
     -30 +-+ *                                                                     *                                                                            ***          * *                    +-+   
             *                                                                                                                                                               * *                          
             *                                                                                                                                                                *                           
         +   *                                 +                                     +                                    +                                     +                                     +   
     -35 +-+ *                                 +                                     +                                    +                                     +                                   +-+   
         0                                     5                                     10                                   15                                    20                                    25  
                                                                                                                                                                                                          
    Y Momentary Loudness (min=-35, max=auto dB) / X Time in seconds


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
