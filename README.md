# UE4Lua
Lua source integration for UE4.

直接在项目中集成 `Lua` 的源码，方便使用

## 测试平台 ##

* 已测试通过
	* `Win32`, `Win64`
	* `Android`
	* `Mac`


* 未测试
	* `Linux`

## 编译问题 ##

### 编译 Android 时出现 no member named decimal_point in struct lconv 错误 ###

需要在 `luaconf.h` 头文件中在以下代码之前

``` cpp
#if !defined(lua_getlocaledecpoint)
#define lua_getlocaledecpoint()		(localeconv()->decimal_point[0])
#endif
```

增加

``` cpp
#if defined(ANDROID)
#define lua_getlocaledecpoint() ('.')
#endif
```