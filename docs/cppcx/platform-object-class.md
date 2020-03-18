---
title: Platform::Object 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Object::Object
- VCCORLIB/Platform::Object::Equals
- VCCORLIB/Platform::Object::GetHashCode
- VCCORLIB/Platform::Object::ReferenceEquals
- VCCORLIB/Platform::ToString
- VCCORLIB/Platform::GetType
helpviewer_keywords:
- Object class
ms.assetid: 709e84a8-0bff-471b-bc14-63e424080b5a
ms.openlocfilehash: 77313f8c4dcc87fa9de852afe2d60e614f8fc3a3
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418346"
---
# <a name="platformobject-class"></a>Platform::Object 類別

提供 Windows 執行階段應用程式中 ref 類別和 ref 結構的一般行為。 所有 ref 類別和 ref 結構執行個體都會隱含轉換為 Platform::Object^，而且也都能覆寫其虛擬 ToString 方法。

## <a name="syntax"></a>語法

```cpp
public ref class Object : Object
```

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[Object：： Object](#ctor)|初始化 Object 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Object：： Equals](#equals)|判斷指定的物件是否等於目前的物件。|
|[Object：： GetHashCode](#gethashcode)|傳回此執行個體的雜湊碼。|
|[Object：： ReferenceEquals](#referenceequals)|判斷指定的物件執行個體是否為相同的執行個體。|
|[ToString](#tostring)|傳回代表目前物件的字串。 可以被覆寫。|
|[GetType](#gettype)|取得可描述目前執行個體的 [Platform::Type](../cppcx/platform-type-class.md) 。|

## <a name="inheritance-hierarchy"></a>繼承階層

`Object`

`Object`

### <a name="requirements"></a>需求

**標頭：** vccorlib.h

**命名空間：** Platform

## <a name="equals"></a>Object：： Equals 方法

判斷指定的物件是否等於目前的物件。

### <a name="syntax"></a>語法

```cpp
bool Equals(
    Object^ obj
)
```

### <a name="parameters"></a>參數

*obj*<br/>
要比較的物件。

### <a name="return-value"></a>傳回值

如果物件相等，**則為 true** ，否則為**false**。

## <a name="gethashcode"></a>Object：： GetHashCode 方法

傳回這個執行個體的 `IUnknown`* 識別值 (如果它是 COM 物件)，或計算的雜湊值 (如果它不是 COM 物件)。

### <a name="syntax"></a>語法

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>傳回值

可唯一識別這個物件的數值。

### <a name="remarks"></a>備註

您可以使用 GetHashCode，在對應中建立物件的索引鍵。 您可以使用[Object：： Equals](#equals)來比較雜湊碼。 如果程式碼路徑非常重要，而且 `GetHashCode` 和 `Equals` 不夠快，您可以下拉到基礎 COM 層，並且進行原生 `IUnknown` 指標比較。

## <a name="gettype"></a>Object：： GetType 方法

傳回描述物件之執行時間類型的[Platform：： Type](../cppcx/platform-type-class.md)物件。

### <a name="syntax"></a>語法

```cpp
Object::GetType();
```

### <a name="property-valuereturn-value"></a>屬性值/傳回值

描述物件之執行時間類型的[Platform：： type](../cppcx/platform-type-class.md)物件。

### <a name="remarks"></a>備註

靜態[類型：： GetTypeCode](../cppcx/platform-type-class.md#gettypecode)可以用來取得代表目前類型的[Platform：： TypeCode 列舉](../cppcx/platform-typecode-enumeration.md)值。 這對於內建類型而言非常有用。 除了[Platform：： String](../cppcx/platform-string-class.md)以外之任何 ref 類別的類型程式碼為 Object （1）。

在 windows Api 中使用[windows：： UI：： Xaml：： Interop：： TypeName](/uwp/api/windows.ui.xaml.interop.typename)類別，這是在 windows 元件和應用程式之間傳遞類型資訊的與語言無關的方式。 T[Platform：： Type 類別](../cppcx/platform-type-class.md)具有在 `Type` 和 `TypeName`之間進行轉換的運算子。

使用[typeid](../extensions/typeid-cpp-component-extensions.md)運算子傳回類別名稱的 `Platform::Type` 物件，例如，在 XAML 頁面之間流覽時：

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

## <a name="ctor"></a>Object：： Object 函數

初始化 Object 類別的新執行個體。

### <a name="syntax"></a>語法

```cpp
public:Object();
```

## <a name="referenceequals"></a>Object：： ReferenceEquals 方法

判斷指定的物件執行個體是否為相同的執行個體。

### <a name="syntax"></a>語法

```cpp
public:static bool ReferenceEquals(  Object^ obj1,   Object^ obj2);
```

### <a name="parameters"></a>參數

*obj1*<br/>
要比較的第一個物件。

*obj2*<br/>
要比較的第二個物件。

### <a name="return-value"></a>傳回值

如果兩個物件相同，則為**true** ;否則**為 false**。

## <a name="tostring"></a>Object：： ToString 方法（C++/cx）

傳回代表目前物件的字串。

### <a name="syntax"></a>語法

```cpp
public:
virtual String^ ToString();
```

### <a name="return-value"></a>傳回值

代表目前物件的字串。 您可以在 ref 類別或結構中覆寫這個方法，提供自訂字串訊息：

```cpp
public ref class Tree sealed
{
public:
    Tree(){}
    virtual Platform::String^ ToString() override
    {
      return "I’m a Tree";
    };
};
```

## <a name="see-also"></a>另請參閱

[Platform 命名空間](platform-namespace-c-cx.md)<br/>
[Platform::Type 類別](platform-type-class.md)<br/>
[類型系統](type-system-c-cx.md)
