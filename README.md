# linc/LuaJIT
Haxe/hxcpp @:native bindings for [LuaJIT](http://luajit.org/).

This is a [linc](http://snowkit.github.io/linc/) library.

---

This library works with the Haxe cpp target only.

---

### Example usage

See test/Test.hx

Be sure to read the Lua documentation  
www.lua.org/manual/5.1/manual.html  

```haxe
import llua.Lua;
import llua.LuaL;
import llua.State;

class Test {
        
    static function main() {

        var lua:State = LuaL.newstate();
        LuaL.openlibs(lua);
        trace("Lua version: " + Lua.version());
        trace("LuaJIT version: " + Lua.versionJIT());

        LuaL.dofile(lua, "script.lua");

        Lua.getglobal(lua, "foo");

        Lua.pushinteger(lua, 1);
        Lua.pushnumber(lua, 2.0);
        Lua.pushstring(lua, "three");

        Lua.pcall(lua, 3, 0, 1);

        Lua.close(lua);
        
    }

}

```

### Note for android:
If you have a ploblem when you compile with linc_luajit like this

```
Error: In file included from include/llua/Lua_helper.h:10:0, from ./src/boot.cpp:787:
C:/HaxeToolkit/haxe/lib/linc_luajit/git//linc/linc_lua.h:3:19: fatal error: E:/therepo/export/release/android/obj/obj/android-v7/__pch/haxe/hxcpp.h: No such file or directory
#include <hxcpp.h>
compilation terminated.
```

Just compile with this code on android like this `lime test android -D NO_PRECOMPILED_HEADERS` if the error happens ONLY
