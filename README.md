[![license](https://img.shields.io/dub/l/vibe-d.svg?maxAge=2592000)]()
![cocoapdos](https://img.shields.io/cocoapods/v/SHJavascriptInterface.svg?style=flat)

# JavascriptInterface

***
## 使用

***

### 1.

使用pod添加到项目中:

```
pod 'SHJavascriptInterface', '~>1.02'
```



### 2.

引入头文件:

```objective-c
import "UIWebView+JavascriptInterface.h"
```

简化JS调用iOS原生方法时的麻烦过程，在初始化时添加javascriptInterface:

```objective-c
[webView addJavascriptInterface:interfaceProvider forName:@"nativeCommon"];
```

并通过interfaceprovider的javascriptInterfaces返回需要js调用的原生方法和js调用名称:

```objective-c
- (NSDictionary<NSString *, NSValue *> *) javascriptInterfaces{
    return @{
             @"callNative" : [NSValue valueWithPointer:@selector(callNative:)]
             };
}
```

对应的原生方法：

```
- (NSString *) callNative:(NSString *) input{
    return [input stringByAppendingString:"-modified-by-native"];
}
```

然后js调用原生方法可以直接写成:

```javascript
var result = nativeCommon.callNative(xxx);
```

