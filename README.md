The current version OpenOffice is not stable on Ubuntu. The Draw application does not finish without errors.
I found two errors when the application is finished:
- memory leak
- segmentation fault (usage deleted destructor)

The corrections added to the files salplug.cxx,Theme.cxx,ToolBarManager.cxx resolves these errors.

Another issue is a crash caused by using the deleted object of the type ServerFont.
The object ServerFont is deleted when the cache has no memory for a new object ServerFont with new font parameters.
Before my corrections were created, two objects ServerFont.
The key can retrieve value both these objects: width = 0 or width=height.
After deleting one of them, the key can retrieve the deleted object.
My correction removes this ambiguity.

If you want to use OpenOffice Draw application, you can download OpenOffice sources from the repository 
and find the files described above, add these corrections. 
After compilation, the OpenOffice Draw application will be more stable.
