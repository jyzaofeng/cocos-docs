# Cocos API风格说明

适用版本：v3.0-beta2及更高版本

## 两阶段构造器及静态create()函数

在cocos2d-x引擎中，我们使用了两阶段构造器，这不仅指Objective-C实现文件（implementation），也与Symbian SDK及Bada SDK相似。我认为这一举措在C++编程中很不错。

```cpp
MyClass::MyClass()  // c++ class constructor
```

我们之所以不应在这里编写任何逻辑，是因为C++默认构造器不能返回表明我们逻辑正确与否的bool 值。

bool MyClass::initWithFilename(const std::string& filename)

MyClass* obj = new MyClass;

在cocos2d-x引擎中，我们已对这一两阶段构造器进行包装，并在静态函数create()中自动释放引用计数。除了单例模式，每一个cocos2d类都有自己的static CCClass* CCClass::create(...)方法。极力推荐这一方法。代码样本：

```cpp


## doSomething()

这是最常见的函数名，在cocos2d-x/-html5引擎中处处都有应用到。第一个字是一个动词，第二个字是一个名词。比如：`replaceScene(CCScene*)` 和 `getTexture()`。

## doWithResource()


class Layer




因为在C++ 和 C++11中没有"property" （“属性”）这个概念，所以我们在Cocos2d-x引擎中使用了许多getter和setters。


改变属性的值。这通常会影响到对象的行为。比如 `_sprite->setPosition(ccp(0,0))` 会将精灵移动到左下角。


```

