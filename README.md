# Text-image-alignment
## Align the text inside the scanned images<br>
To remove the skewness, angle of skewness needs to be calculated first and image is rotated as per the angle.<br> 
**Calculating the angle of skewness**<br>
To calculate the angle:
1. Convert the image to gray
2. Apply some blur to deacrease the noise in the image
3. Invert the image so that the text become white and background noise
4. Perform dilation to expand the white pixel so that white pixels form a line.<br>
   ```kernel = cv2.getStructuringElement(cv2.MORPH_RECT, (30, 5))```<br>
   ```dilate = cv2.dilate(thresh, kernel, iterations=5)```<br>
   using larger kernel on X to merge characters together into a line but use smaller kernel of Y to separate lines.
5. Then, we find all the contours, and use minimum area rectange to calculate angle<br>
    ```angle = cv2.minAreaRect(c)[-1]```<br>
    **Min. Area Rectangle:**<br>
    As is clear from the name, the bounding rectangle is drawn with a minimum area.The below image shows 2 rectangles, the green one is the normal bounding rectangle while the red one is the minimum area rectangle.<br>
    ![image](https://user-images.githubusercontent.com/20660098/130480219-e36ab995-5f20-4b63-b2a3-60b45e0e0dac.png)
    
Ref: https://docs.opencv.org/

