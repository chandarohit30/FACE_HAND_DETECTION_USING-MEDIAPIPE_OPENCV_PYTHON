# FACE_HAND_DETECTION_USING-MEDIAPIPE_OPENCV_PYTHON

by using Haar Casacde Algorithm we can acheive or recognize the face on the image capture device 

opencv and mediapipe are the librabries which we are using in this project 

we need to import handdetector library for detecting hand on the screen for measuring the distance between two fingers we need import math library import time library for the time on the screen or image capture device 

For the array of elements of the picture into an array elements we are importing numpy library
def findHands(self, img, draw=True):
        imgRGB = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
        self.results = self.hands.process(imgRGB)
        # print(results.multi_hand_landmarks)

        if self.results.multi_hand_landmarks:
            for handLms in self.results.multi_hand_landmarks:
                if draw:
                    self.mpDraw.draw_landmarks(img, handLms,self.mpHands.HAND_CONNECTIONS)
        return img
finger path detectioon ways 
def fingersUp(self):
        fingers = []
        # Thumb
        if self.lmList[self.tipIds[0]][1] > self.lmList[self.tipIds[0] - 1][1]:
            fingers.append(1)
        else:
            fingers.append(0)
        # 4 Fingers
        for id in range(1, 5):
            if self.lmList[self.tipIds[id]][2] < self.lmList[self.tipIds[id] - 2][2]:
                fingers.append(1)
            else:
                fingers.append(0)
        return fingers
