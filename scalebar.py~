from PIL import Image
from PIL import ImageDraw
from PIL import ImageFont
from os import getcwd, listdir

# examine the current directory for files and make a list of those files
cwd = getcwd()
filelist = listdir(cwd)

# this is a list of possible images types.  feel free to expand it.
# at the moment this program only supports three-letter extensions.
imagetypes = ['.jpg', '.png', '.tif', '.gif']
photolist = []

# make a new list that only includes images
for i in imagetypes:
    for j in filelist:
        if j.lower().endswith(i):
            photolist.append(j)
            
if photolist == []:
    print 'There are no photos in this diretory'

# function for determining which scale bar label to use.  length of the 
# scale bar is related to the width of the image. this assumes that the
# filenames include the scale string. for example 'photo001-25x.png'
# would indicate a 25 x 
def scalelabel(i):
    if '25x' in i:
        scalelabel = '1 mm'
    elif '40x' in i:
        scalelabel = '250 um'
    elif '100x' in i:
        scalelabel = '100 um'
    elif '250x' in i:
        scalelabel = '40 um'
    elif '400x' in i:
        scalelabel = '25 um'
    elif '500x' in i:
        scalelabel = '20 um'
    else:
        scalelabel = 'error'
    return scalelabel
    
# scale color
linecolor = (255, 255, 255)

# assess each photo in the directory, draw a scale bar and add text,
# then resave each photo with a new name.
for i in photolist:
    if i.startswith('scale_'):
        pass
    else:
        newname = 'scale_' + i
        im = Image.open(i)
        imx = im.size[0]
        imy = im.size[1]
        mag = 0.114 * imx
        label = scalelabel(i)
        if label == 'error':
            print 'Either %s is labeled incorrectly, or '\
            'that scale does not yet have a definition in the '\
            'program.\n' % i
        else:
            # define the font to use.  this will be in a different 
            # location in Windows
            fntsize = int(36 * (imx / 1920.))
            fnt = ImageFont.truetype('/usr/share/fonts/truetype/'\
            'freefont/FreeMonoBold.ttf', fntsize)
            fntcolor = (255, 255, 255)
            # scale placement parameters relative to size of photo
            linex1 = imx - (imx / 10) - mag
            linex2 = (imx - (imx / 10))
            liney = imy - (imy / 10)
            # scale placement
            draw = ImageDraw.Draw(im)
            draw.line([(linex1, liney), \
            (linex2, liney)], fill = linecolor, width = 10)
            # label placement
            draw.text(((imx - (imx / 10) - (mag / 1.33)), \
            imy - (imy / 10) - (imy / 20)), label, font = fnt, \
            fill = fntcolor)
            im.save(newname)
            print '%s has been re-saved with a scale bar as'\
            ' %s.\n' % (i, newname)

#eof
