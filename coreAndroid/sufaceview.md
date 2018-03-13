* SurfaceView can be updated on the background thread.
* SurfaceView has dedicate surface buffer while all the view share one surface buffer that is allocated by ViewRoot. In another word,sufaceView cost more resources.
* SurfaceView can not be hardware accelerated\(as of JB4.2\)while 95% oprations on normal View are HW accelerated using openGL ES.
* More work should be done to create your customized surfaceView.You need to listener to the surfaceCreated/Destroy Event.create an render thread, more importantly,synchronized the render thread and main thread. However,to customize the View,all you need to do is override `onDraw` method.



