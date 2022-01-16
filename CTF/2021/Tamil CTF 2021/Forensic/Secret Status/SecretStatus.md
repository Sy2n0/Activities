# Secret Status

- Author : 0xcyberpj
- Category : Forensic
- Description : Jo Praveen finds something suspicious from PJ's status to his GF

Challenges file   
https://drive.google.com/file/d/1OCI6Xt2R-xnGjACZ2JlbsPoqoWeh8swQ/view?usp=sharing
**Please understand that the file was uploaded through Google drive because it was large in size.**

<hr>

# Write up
When the file was decompressed, there was an mp4 file.   
I thought it was audio steganography.

In the video, I could hear a strange sound around 20 seconds, and then I heard a strange sound once again about 29 seconds to 30 seconds.

I thought I should extract audio that sounded strange in this part, and I wrote the following code.

```
import moviepy.editor
video=moviepy.editor.VideoFileClip("video.mp4")
audio=video.audio
audio.write_audiofile("Flag.mp3")
print("|Flag|")
```

As a result, flag.We were able to successfully extract mp3.
<img width="1158" alt="Screen Shot 2021-09-29 at 6 07 33 PM" src="https://user-images.githubusercontent.com/84657474/135238633-8c4aef09-39a1-4092-95f2-673bf4a5832e.png">

After that, the spectrum was checked using sonic visualizer.

In this part, I was able to check a part of the first flag.   
```TamilCTF{i_10```
<img width="1792" alt="Screen Shot 2021-09-29 at 6 09 25 PM" src="https://user-images.githubusercontent.com/84657474/135238913-e253ec10-7ce6-48ff-a494-def65f28bcfc.png">

Then I went over to the right and was able to check the last part of the second flag.   
```v3_y0u}```
<img width="1792" alt="Screen Shot 2021-09-29 at 6 11 20 PM" src="https://user-images.githubusercontent.com/84657474/135239252-70a1b68f-25d3-4d71-9870-a99bd355b9a2.png">

Flag is ```TamilCTF{i_10v3_y0u}```
