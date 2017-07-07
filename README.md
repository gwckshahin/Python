# Python
Below is the obamicon.py file:


from PIL import Image
im=Image.open("mushi.jpg")
im.rotate(45).show()
new_image=Image.new(im.mode,im.size)
new_image.save("output.jpg","jpeg")



#putdata
#im.putdata(data)
#im.putdata(data, scale, offset)

# RGB values for recoloring.
darkBlue = (0, 51, 76)
red = (217, 26, 33)
lightBlue = (112, 150, 158)
yellow = (252, 227, 166)
# values for dark
black= (0,0,0)
light_black=(32, 32, 32)
grey=(72,72,72)
light_grey=(152,152,152)

# Import image.
my_image = Image.open("mushi.jpg") #change IMAGENAME to the path on your computer to the image you're using
image_list = my_image.getdata() #each pixel is represented in the form (red value, green value, blue value, transparency). You don't need the fourth value.
image_list = list(image_list) #Turns the sequence above into a list. The list can be iterated through in a loop.


recolored = [] #list that will hold the pixel data for the new image.


#YOUR CODE to loop through the original list of pixels and build a new list based on intensity should go here.
question=input("Choose theme: America or Dark")

if question=="America":

    for color in image_list:
        p=color[0]+color[1]+color[2]
        if p<182:
            recolored.append(darkBlue)
        elif 182<=p<=364:
            recolored.append(red)
        elif 364<=p<=546:
            recolored.append(lightBlue)
        elif p>546:
            recolored.append(yellow)


if question=="Dark":
    for color in image_list:
        p=color[0]+color[1]+color[2]
        if p<182:
            recolored.append(black)
        elif 182<=p<=364:
            recolored.append(light_black)
        elif 364<=p<=546:
            recolored.append(grey)
        elif p>546:
            recolored.append(light_grey)
else:
    print(ok)






 # Create a new image using the recolored list. Display and save the image.
new_image = Image.new("RGB", my_image.size) #Creates a new image that will be the same size as the original image.
new_image.putdata(recolored) #Adds the data from the recolored list to the image.
new_image.show() #show the new image on the screen
new_image.save("recolored.jpg", "jpeg") #save the new image as "recolored.jpg"