## Session 7 June 16, Monday

### What I learned

**cv.VideoWriter**
- Takes four arguments: output file path, codec, fps, frame size tuple (width, height)
- Must be initialized before the while loop creating it inside the loop resets the file every frame
- Frame size must match actual frame dimensions exactly mismatch corrupts the output file
- Release after the loop alongside VideoCapture same pattern, same reason

**fourcc**
- Four character code that specifies the video codec compression and encoding algorithm
- cv.VideoWriter_fourcc(*'mp4v') for .mp4 output
- The * unpacks the string into four separate characters as required by the function

**FPS matching**
- Output FPS must match input FPS mismatch causes slow motion, fast forward, or choppy playback
- Retrieved from VideoCapture using cv.CAP_PROP_FPS before the loop
- Each video gets its own FPS variable in case they differ

**Frame dimensions from VideoCapture**
- Retrieved using cv.CAP_PROP_FRAME_WIDTH and cv.CAP_PROP_FRAME_HEIGHT
- Must wrap in int() property returns float, VideoWriter requires integers
- Retrieved from VideoCapture object before loop, not from frame inside loop

### What I built
- Stage 8: VideoWriter initialized for both Kathmandu and Highway outputs
- Processed frame copies written to Output/ folder each loop iteration
- Both writers released properly after loop alongside VideoCapture objects
- Output files: Output/output_kathmandu.mp4 and Output/output_highway.mp4
- Classical pipeline now complete all 8 stages built and running

### Observations Output Videos
- Kathmandu output: lines flicker to different angles every frame, tracking building edges and noise no consistent lane detection throughout entire video
- Highway output: left lane line stable and consistently tracking yellow marking right dashed line flickers between frames, sometimes replaced by outer shoulder line when dashes disappear
- Highway occasionally catches shoulder line instead of dashed center line ROI triangle wide enough to include road shoulder

### Key research finding Stage 8 and baseline complete
The completed classical pipeline produces two qualitatively different outputs.
Highway: stable left lane detection, partially stable right lane detection, occasional false positives from road shoulder.
Kathmandu: no lane detection at any point in the video. Lines present every frame but tracking noise sources only.
The pipeline cannot be tuned to work on Kathmandu footage there is no parameter adjustment
that creates signal where none exists in the environment.
This completes the classical baseline. All subsequent work builds on this documented failure.