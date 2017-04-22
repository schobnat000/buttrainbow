# buttrainbow
nope
# copy the following

import simplegui, time, random

class Constants:

    WINDOW_WIDTH = 500
    WINDOW_HEIGHT = WINDOW_WIDTH
    GLOBAL_DEFAULT_SQUARE_SIZE = 25

    GRID_WIDTH = WINDOW_WIDTH / GLOBAL_DEFAULT_SQUARE_SIZE
    GRID_HEIGHT = GRID_WIDTH
class Rect:
    
    def rect_coords (length, height, startpos = (0, 0)) :
        x = startpos[0]
        y = startpos[1]
        return [
            (x, y),
            (x, y + height),
            (x + length, y + height),
            (x + length, y)  
        ] 

    class Square:
        
        DEFAULT_SQUARE_DRAW_ATTRIBUTES = {
            "line_width": 2,
            "line_color": 'White',
            "fill_color": 'Orange'
        }        

        SHAPE_ATTRIBUTES = DEFAULT_SQUARE_DRAW_ATTRIBUTES
        SIZE = Constants.GLOBAL_DEFAULT_SQUARE_SIZE

        def __init__(self, top_left_pt, size=SIZE, shape_attributes=SHAPE_ATTRIBUTES, color=None):
            self.top_left_point = top_left_pt
            self.shape_attributes = dict(shape_attributes)
            self.size = size
            if color:
                self.set_color(color)
        
        def set_color(self, color):
            self.shape_attributes["fill_color"] = color
            
        def draw_me(self, canvas):
            size = self.size
            (x,y) = self.top_left_point
            (x,y) = x*size, y*size
            canvas.draw_polygon(Rect.rect_coords(size, size, (x,y)),
                self.shape_attributes["line_width"],
                self.shape_attributes["line_color"],
                self.shape_attributes["fill_color"]
            )
#

sqrs = []

a1 = Rect.Square((0,0), color="Red")
b1 = Rect.Square((1,1), color="Orange")
c1 = Rect.Square((2,2), color="Yellow")
d1 = Rect.Square((3,3), color="Green")
e1 = Rect.Square((4,4), color="Blue")
f1 = Rect.Square((5,5), color="Purple")
g1 = Rect.Square((6,6), color="Brown")
h1 = Rect.Square((7,7), color="Red")
i1 = Rect.Square((8,8), color="Orange")
j1 = Rect.Square((9,9), color="Yellow")
k1 = Rect.Square((10,10), color="Green")
l1 = Rect.Square((11,11), color="Blue")
m1 = Rect.Square((12,12), color="Purple")
n1 = Rect.Square((13,13), color="Brown")
o1 = Rect.Square((14,14), color="Red")
p1 = Rect.Square((15,15), color="Orange")
q1 = Rect.Square((16,16), color="Yellow")
r1 = Rect.Square((17,17), color="Green")
s1 = Rect.Square((18,18), color="Blue")
t1 = Rect.Square((19,19), color="Purple")
sqrs.extend([a1, b1, c1, d1, e1, f1, g1, h1, i1, j1, k1, l1, m1, n1, o1, p1, q1, r1, s1, t1])

                               
def draw(canvas):
    for sqr in sqrs:
        sqr.draw_me(canvas)

class Graphics:   
    WINDOW_WIDTH = Constants.WINDOW_WIDTH
    WINDOW_HEIGHT = Constants.WINDOW_HEIGHT
    
    def __init__(self, width=WINDOW_WIDTH, height=WINDOW_HEIGHT):
        frame = simplegui.create_frame("Home", width, height)
        frame.set_canvas_background("Silver")
        frame.set_draw_handler(draw)
        frame.start()        
#              
Graphics()

# it's useless
