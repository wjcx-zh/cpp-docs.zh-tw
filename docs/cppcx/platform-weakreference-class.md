---
title: Platform::WeakReference 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- Platform::WeakReference
ms.assetid: 8cfe1977-a8c7-4b7b-b539-25c77ed4c5f1
ms.openlocfilehash: befefba7cc76f24f6dddd58d0c5f040bfd205508
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216592"
---
# <a name="platformweakreference-class"></a>Platform::WeakReference 類別

表示 ref 類別之執行個體的弱式參考。

## <a name="syntax"></a>語法

```cpp
class WeakReference
```

#### <a name="parameters"></a>參數

### <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|成員|說明|
|------------|-----------------|
|[WeakReference：： WeakReference](#ctor)|初始化 WeakReference 類別的新執行個體。|

### <a name="methods"></a>方法

|成員|說明|
|------------|-----------------|
|[WeakReference：： Resolve](#resolve)|傳回基底 ref 類別的控制代碼。如果物件已不存在則傳回 nullptr。|

### <a name="operators"></a>運算子

|成員|說明|
|------------|-----------------|
|[WeakReference::operator=](#operator-assign)|指派新值給 WeakReference 物件。|
|[WeakReference::operator BoolType](#booltype)|執行安全的 bool 模式。|

### <a name="remarks"></a>備註

WeakReference 類別本身不是 ref 類別，因此不會繼承 Platform::Object^，而且也不能在公用方法的簽章中使用。

## <a name="weakreferenceoperator"></a><a name="operator-assign"></a>WeakReference：： operator =

指派值給 WeakReference。

### <a name="syntax"></a>語法

```cpp
WeakReference& operator=(decltype(__nullptr));
WeakReference& operator=(const WeakReference& otherArg);
WeakReference& operator=(WeakReference&& otherArg);
WeakReference& operator=(const volatile ::Platform::Object^ const otherArg);
```

### <a name="remarks"></a>備註

上述清單中的最後一個多載可讓您指派 ref 類別給 WeakReference 變數。 在此情況下，ref 類別會轉換成[Platform：： Object](../cppcx/platform-object-class.md)^。 您稍後會在[WeakReference：： Resolve \<T> ](#resolve)成員函式中指定為類型參數的引數，以還原原始類型。

## <a name="weakreferenceoperator-booltype"></a><a name="booltype"></a>WeakReference：： operator BoolType

為 WeakReference 類別實作安全 bool 樣式。 無法從程式碼中明確呼叫。

### <a name="syntax"></a>語法

```cpp
BoolType BoolType();
```

## <a name="weakreferenceresolve-method-platform-namespace"></a><a name="resolve"></a>WeakReference：： Resolve 方法（Platform 命名空間）

傳回原始 ref 類別的控制碼， **`nullptr`** 如果物件已不存在，則傳回。

### <a name="syntax"></a>語法

```cpp
template<typename T>
T^ Resolve() const;
```

### <a name="parameters"></a>參數

### <a name="property-valuereturn-value"></a>屬性值/傳回值

之前與 WeakReference 物件相關聯之 ref 類別的控制代碼，或者是 nullptr。

### <a name="example"></a>範例

```cpp
Bar^ bar = ref new Bar();
//use bar...

if (bar != nullptr)
{
    WeakReference wr(bar);
    Bar^ newReference = wr.Resolve<Bar>();
}
```

請注意，類型參數是 T 而非 T^。

## <a name="weakreferenceweakreference-constructor"></a><a name="ctor"></a>WeakReference：： WeakReference 函式

提供各種建構 WeakReference 的方式。

### <a name="syntax"></a>語法

```cpp
WeakReference();
WeakReference(decltype(__nullptr));
WeakReference(const WeakReference& otherArg);
WeakReference(WeakReference&& otherArg);
explicit WeakReference(const volatile ::Platform::Object^ const otherArg);
```

### <a name="example"></a>範例

```cpp
MyClass^ mc = ref new MyClass();
WeakReference wr(mc);
MyClass^ copy2 = wr.Resolve<MyClass>();
```

## <a name="see-also"></a>另請參閱

[平台命名空間](../cppcx/platform-namespace-c-cx.md)
