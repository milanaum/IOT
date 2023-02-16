

***********************************************************************************************************************
Project: Eye ball cursor code<br>

import sys<br>
import time<br>
import Quartz<br>
class Mouse():<br>
    down = [Quartz.kCGEventLeftMouseDown, Quartz.kCGEventRightMouseDown, Quartz.kCGEventOtherMouseDown]<br>
    up = [Quartz.kCGEventLeftMouseUp, Quartz.kCGEventRightMouseUp, Quartz.kCGEventOtherMouseUp]<br>
    [LEFT, RIGHT, OTHER] = [0, 1, 2]<br>
    def position(self):<br>
        point = Quartz.CGEventGetLocation( Quartz.CGEventCreate(None) )<br>
        return point.x, point.y<br>
    def __mouse_event(self, type, x, y):<br>
        mouse_event = Quartz.CGEventCreateMouseEvent(None, type, (x, y), Quartz.kCGMouseButtonLeft)<br>
        Quartz.CGEventPost(Quartz.kCGHIDEventTap, mouse_event)<br>
    def move(self, x, y):<br>
        self.__mouse_event(Quartz.kCGEventMouseMoved, x, y)<br>
        Quartz.CGWarpMouseCursorPosition((x, y))<br>
    def press(self, x, y, button=0):<br>
        event = Quartz.CGEventCreateMouseEvent(None, Mouse.down[button], (x, y), button)<br>
        Quartz.CGEventPost(Quartz.kCGHIDEventTap, event)<br>
    def release(self, x, y, button=0):<br>
        event = Quartz.CGEventCreateMouseEvent(None, Mouse.up[button], (x, y), button)<br>
        Quartz.CGEventPost(Quartz.kCGHIDEventTap, event)<br>
    def doubleClick(self, x, y, clickCount, button=0):<br>
        print("Double click event")<br>
        theEvent = Quartz.CGEventCreateMouseEvent(None, Mouse.down[button], (x, y), button)<br>
        Quartz.CGEventSetIntegerValueField(theEvent, Quartz.kCGMouseEventClickState, clickCount)<br>
        Quartz.CGEventPost(Quartz.kCGHIDEventTap, theEvent)<br>
        Quartz.CGEventSetType(theEvent, Quartz.kCGEventLeftMouseUp)<br>
        Quartz.CGEventPost(Quartz.kCGHIDEventTap, theEvent)<br>
        Quartz.CGEventPost(Quartz.kCGHIDEventTap, theEvent)<br>
        Quartz.CGEventSetType(theEvent, Quartz.kCGEventLeftMouseDown)<br>
        Quartz.CGEventPost(Quartz.kCGHIDEventTap, theEvent)<br>
        Quartz.CGEventSetType(theEvent, Quartz.kCGEventLeftMouseUp)<br>
        Quartz.CGEventPost(Quartz.kCGHIDEventTap, theEvent)<br>
        print("Double click event ended")<br>
    def click(self, button=0):<br>
        x, y = self.position()<br>
        self.press(x, y, button)<br>
        self.release(x, y, button)<br>
    def click_pos(self, x, y, button=0):<br>
        self.move(x, y)<br>
        self.click(button)<br>
    def torelative(self, x, y):<br>
        curr_pos = Quartz.CGEventGetLocation( Quartz.CGEventCreate(None) )<br>
        x += curr_pos.x;<br>
        y += curr_pos.y;<br>
        return [x, y]<br>
    def move_rel(self, x, y):<br>
        [x, y] = self.torelative(x, y)<br>
        moveEvent = Quartz.CGEventCreateMouseEvent(None, Quartz.kCGEventMouseMoved, Quartz.CGPointMake(x, y), 0)<br>
        Quartz.CGEventPost(Quartz.kCGHIDEventTap, moveEvent)<br>
    def mouseEvent(self, type, posx, posy):<br>
        theEvent = Quartz.CGEventCreateMouseEvent(None, type, (posx,posy), Quartz.kCGMouseButtonLeft)<br>
        Quartz.CGEventPost(Quartz.kCGHIDEventTap, theEvent)<br>
    def mousedrag(self, posx, posy):<br>
        self.mouseEvent(Quartz.kCGEventLeftMouseDragged, posx,posy)<br>
if __name__ == '__main__':<br>
    mouse = Mouse()<br>
    if sys.platform == "darwin":<br>
        print("Current mouse position: %d:%d" % mouse.position())<br>
        print("Moving to 100:100...");<br>
        mouse.move_rel(25, 16)<br>
        print("Clicking 200:200 position with using the right button...");<br>
        #mouse.click_pos(25, 16, 0)<br>
        #mouse.click_pos(25, 16, 0)<br>
        #mouse.click_pos(25, 16, 0)<br>
        print("Clickingthe right button...");<br>
        mouse.move(25, 26)<br>
        time.sleep(0.05)<br>
        mouse.move(35, 26)<br>
@@ -95,9 +91,9 @@ def mousedrag(self, posx, posy):<br>
        time.sleep(0.05)<br>
        mouse.click_pos(1264, 416, 1)<br>
        mouse.doubleClick(1264, 46, 2, 0)<br>


        #mouse.doubleClick(25, 26, 2, 0)<br>

    elif sys.platform == "win32":<br>
        print("Error: Platform not supported!")<br>
	
	
	***************************************************************************************************
	
	https://www.kaggle.com › shrutimechlearn › eye-move.. bird species<br>
	

https://github.com › manideepc › Bird-Species-Identifia... <br> code<br>

Bird-Species-Recognition - Machine Learning Project - GitHubhttps://github.com › SwatiNH › Bird-Species-Recognition<br>
https://www.kaggle.com/code/fareselmenshawii/birds-450-species-images-classification/notebook,<br>
https://www.kaggle.com/code/abduulrahmankhalid/birds-species-prediction-mobilenetv2-acc-95 <br>
https://www.kaggle.com/code/emreiekyurt/bird-species-classification-with-deep-learning<br>
https://www.kaggle.com/datasets/coolerextreme/cub-200-2011?resource=download <br>
https://www.kaggle.com/code/emreiekyurt/bird-species-classification-with-deep-learning <br>
https://www.kaggle.com/gpiosenka/100-bird-species<br>
https://github.com/LaurentVeyssier/Bird_Classifier_Tensorflow_Colab_Notebook>br>
https://www.kaggle.com/code/emreiekyurt/bird-species-classification-with-deep-learning<br>
https://www.kaggle.com/code/vencerlanz09/bird-classification-using-cnn-mobilenetv2<br>
https://medium.com/jovianml/cnn-and-transfer-learning-with-pytorch-200-bird-species-image-classification-7e1f2e958a78<br>
https://www.kaggle.com/code/sharansmenon/pytorch-cubbirds200-classification<br>
