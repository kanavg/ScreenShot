# ScreenShot
Modified Android Framework to take a screenshot when you double tap on the top left part of the screen.

Files modified/added:
frameworks/native/include/android/input.h
frameworks/native/services/inputflinger/InputReader.cpp
frameworks/native/services/inputflinger/InputReader.h
frameworks/base/core/java/android/view/MotionEvent.java
frameworks/base/policy/src/com/android/internal/policy/impl/PhoneWindowManager.java
frameworks/base/core/java/com/android/internal/widget/ TopLeftPointerLocationView.java

Solution

InputFlinger and Native classification library: I added another method in TouchInputMapper. For all the touch points we receive, I check if it is in the top left corner and if it is I update the tool type.

PointerEventListener: I created a new listener called TopLeftPointerLocationView which would get a onPointerEvent callback. I created a gesture listener which would also get a callback on double tap. If the double tap occurred and our custom tool type was set I would trigger a system screenshot.


