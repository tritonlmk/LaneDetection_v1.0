

# **Finding Lane Lines on the Road** 



### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I use Canny Edge Detection to detect edges then I use Hough Transform to collect lines and finally draw lines in a certain region

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by first collection slopes of the lines of the output of Hough transform. Then divide them into two groups and calculate the mean of slopes and interception of each group to be the final lanelines slope and interception

the method used in the modified draw_lines() are simple, I will use a more precise one later. Why I did not just polyfit the end points of the collected lines(although it works better than my method, I have tested....) is that : the two points are associated points, and polyfit function just ignore those connections, I think it is not the optimal solution.

I will write a function which will output two groups of number(given one group of number), making differences inside each group small and differences between two groups as big as possible. Also, noise(incorrect lanelines representation and "horizental" line will be droped automatically)


I do not use the helper functions. I use the functions provided in the course, mostly


### 2. Identify potential shortcomings with current pipeline


The shortcomings of this program is clear, the first one is that the date clustering method in the modified draw_lines() is simple and imprecise. as for a big gap may exist between the quantity of lines detected belonging to the right and left lanelines, using the numpy.mean is not a good method. Refined mehtods will be proviede regarding clustering the slopes gathered.

When modified draw_lines() are not used, the result seems good, but when using this function, it comes to mass.


### 3. Suggest possible improvements to pipeline

Great improvements coulde
