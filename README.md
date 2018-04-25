# ImageProcessing
Small image processing library
Functions:

    1) convert color image to greyscale
    2) crop an image
    
----

### To see the functions working in action, there are some examples at the bottom of the jupyter notebook. 

#### Gray Scaling an image

Equation for greyscale conversion comes from:
https://en.wikipedia.org/wiki/Grayscale#Converting_color_to_grayscale

    
    a) Y' = 0.299 R + 0.587 G + 0.114 B <-- at the pixel level
    
Note: At least with matplotlib, given the format how I have made the image in grayscale, when plotting the image matrix, you must tell the function to draw the result with the gray color mapping. If you don't then the computer will try to interpolate the ranges present into some color range.
```
plt.imshow(imageMatrix, cmap = plt.get_cmap('gray'))
```

#### Cropping

By definition, cropping does not allow access to outside of the image. Therefore, if the user puts in a value beyond the appropriate ranges (either too small or too large), those values hit an exception. The other possible option would be to manually map the extreme values to 0 or image.shape constraints; however, I chose not to do that since it would involve editing the user's choices. 

Furthermore, the cropImage function can take in either two opposing corners ((a and d) or (b and c)) of the box you want to crop out.
```
    a -- b
    |    |
    c -- d
```
The function itself will take those and make it into an image defined with 
```
    p1 = (minX, minY) 
    and 
    p2 = (maxX, minY)
    
 ----------------------
    
       -- p2
    |     |
    p1 -- 
    
 (0,0)
```
The limititaion of this method is that I am only allowing you to crop sub-images which are axis-perpedicular (where in this case the edges of the images are your axes). 

Note about cropping ranges:

Normally, one thinks about ordered pairs in terms of (x, y) := x*(1, 0) + y*(0, 1)

However, with how things are set up here things are reversed. The ordered pairs are (y, x) if you're looking at the picture as if it were the xy plane.

----

## IMPORTANT NOTE:

In the jupyter notebook, the functions are all global in scope. Inside the .py file, they have been encapsulated into a class to make for ease of use and to allow for the file to be imported into other files easily. 
