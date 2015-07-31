# BorderlessEmacs
Compiled Emacs 24 app for OSX with removed border.
For best effects, combine with [MenuAndDockless](http://createlivelove.com/967/menuanddockless-for-yosemite-alpha/) and a Window Manager.
### Screenshots
![alt tag](https://github.com/nikhilunni/BorderlessEmacs/blob/master/screenshots/screenshot1.png)

### Patch
The patch applied to the emacs-24 branch of [git://git.savannah.gnu.org/emacs.git](git://git.savannah.gnu.org/emacs.git) is:
`````diff
index 08b8e3a..8880e9f 100644
--- a/src/nsterm.m
+++ b/src/nsterm.m
@@ -6117,9 +6117,6 @@ if (cols > 0 && rows > 0)
   win = [[EmacsWindow alloc]
             initWithContentRect: r
                       styleMask: (NSResizableWindowMask |
-#if MAC_OS_X_VERSION_MAX_ALLOWED >= MAC_OS_X_VERSION_10_7
-                                  NSTitledWindowMask |
-#endif
                                   NSMiniaturizableWindowMask |
                                   NSClosableWindowMask)
                         backing: NSBackingStoreBuffered
`````

### Build
```bash
git clone git://git.savannah.gnu.org/emacs.git
cd emacs
git checkout emacs-24
patch src/nsterm.m emacs.patch
make configure
./configure --with-ns
make install
open nextstep/Emacs.app
```
