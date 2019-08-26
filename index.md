## VLC-Android Work towards adding automated testing

During the summer 2019, I participated in the Google Summer of Code program with the VideoLAN non profit.

### Context

VLC-Android uses a project called Medialibrary to handle file indexing and all subsequent querries to these files.

The Medialibrary is a C++ program, which is not out of the box usable on Android. To use if you have to make a JNI Wrapper (Java Native Interface), which is code that connects C to Java, and a java wrapper to call the JNI methods.
In short this part of VLC-Android is called the Medialibrary Wrapper.

### The mission

I was asked to abstract all classes in the wrapper that called native code (that called the medialibrary through JNI), so that I could add a stub of the Medialibrary for testing purposes.

There are three kind of automated tests in Android:
- Unit tests, they run on you computer in a VM, and method logic
- Integration tests, they run on a device or in a VM, an test the interactions between components of your app
- UI tests, they test the ui by navigating the app, pressing buttons, checking that elements are present, etc...

To test VLC-Android on a VM when the Medialibrary is involved, we would need to load files so that it could work, and that would take time and space, hence not practicle.
Because of that a stub, with a behaviour consistent with the medialibrary greatly simplifies automated testing for this projects.

### The work

My work on this can be resumed to a few merge requests on VideoLAN's gitlab, you can find them below:

https://code.videolan.org/videolan/vlc-android/merge_requests/136

https://code.videolan.org/videolan/vlc-android/merge_requests/217
