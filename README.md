About
=====
Create a video stream from a user's webcam and attempts do detect smiles in the video.
Based on HAAR detector by Nikos M which is in turn based on Viola-Jones Haar Detection algorithm.

Check out a working demo: http://hpt.co.il/smile/
Dependencies
============
Haar-detector by Nikos M is required and included in this repo.

Usage
=====
1.Add both scripts to the top of the body tag:

    <script type="text/javascript" src="js/haar-detector.js"></script>
    <script type="text/javascript" src="js/smile-detector.js"></script>

2.Add a video tag to the document. If you do not want it to be seen by the user simply change the visibility.

    <video id="vid" height="426" width="640" style="visibility:hidden;" autoplay></video>

3.Create a smile detection callback function:

    var cb = function(isSmile){
        if (isSmile){
            document.getElementById("smile").setAttribute("class", "happy");
        }
        else{
            document.getElementById("smile").setAttribute("class", "sad");
        }
    }


4.Set up the smile detector:

    var sd = new SmileDetector("vid");
    sd.onSmile(cb);

5.Start the smile detection loop on the video stream. The detector will do its best effort to check for a smile every "interval" seconds:

    sd.start(300);
