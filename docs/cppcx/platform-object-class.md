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
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781012"
---
# <a name="platformobject-class"></a>Platform::Object 類別

提供一般行為的 ref 類別或 ref 結構在 Windows 執行階段應用程式。 所有 ref 類別和 ref 結構執行個體都會隱含轉換為 Platform::Object^，而且也都能覆寫其虛擬 ToString 方法。

## <a name="syntax"></a>語法

```cpp
public ref class Object : Object
```

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[Object::Object](#ctor)|初始化 Object 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Object::Equals](#equals)|判斷指定的物件是否等於目前的物件。|
|[Object::GetHashCode](#gethashcode)|傳回這個執行個體的雜湊碼。|
|[Object::ReferenceEquals](#referenceequals)|判斷指定的物件執行個體是否為相同的執行個體。|
|[ToString](#tostring)|傳回代表目前物件的字串。 可以被覆寫。|
|[GetType](#gettype)|取得可描述目前執行個體的 [Platform::Type](../cppcx/platform-type-class.md) 。|

## <a name="inheritance-hierarchy"></a>繼承階層

`Object`

`Object`

### <a name="requirements"></a>需求

**標頭：** vccorlib.h

**命名空間：** Platform

## <a name="equals"></a> Object:: equals 方法

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

**真**如果物件相等，否則為**false**。

## <a name="gethashcode"></a>  Object:: gethashcode 方法

傳回這個執行個體的 `IUnknown`* 識別值 (如果它是 COM 物件)，或計算的雜湊值 (如果它不是 COM 物件)。

### <a name="syntax"></a>語法

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>傳回值

可唯一識別這個物件的數值。

### <a name="remarks"></a>備註

您可以使用 GetHashCode，在對應中建立物件的索引鍵。 您可以使用來比較雜湊程式碼[object:: equals](#equals)。 如果程式碼路徑非常重要，而且 `GetHashCode` 和 `Equals` 不夠快，您可以下拉到基礎 COM 層，並且進行原生 `IUnknown` 指標比較。

## <a name="gettype"></a>  Object:: gettype 方法

傳回[platform:: type](../cppcx/platform-type-class.md)描述物件的執行階段類型的物件。

### <a name="syntax"></a>語法

```cpp
Object::GetType();
```

### <a name="property-valuereturn-value"></a>屬性值/傳回值

A [platform:: type](../cppcx/platform-type-class.md)描述物件的執行階段類型的物件。

### <a name="remarks"></a>備註

靜態[type:: gettypecode](../cppcx/platform-type-class.md#gettypecode)可用來取得[platform:: typecode 列舉](../cppcx/platform-typecode-enumeration.md)值，表示目前的類型。 這對於內建類型而言非常有用。 除了任何 ref 類別的類型代碼[platform:: string](../cppcx/platform-string-class.md)是 Object (1)。

[Windows::UI::Xaml::Interop::TypeName](/uwp/api/windows.ui.xaml.interop.typename)類別用來與語言無關的方式的 Windows 元件和應用程式之間傳遞類型資訊的 Windows Api。 T[platform:: type 類別](../cppcx/platform-type-class.md)有之間進行轉換的運算子`Type`和`TypeName`。

使用[typeid](../extensions/typeid-cpp-component-extensions.md)運算子傳回`Platform::Type`類別名稱，例如 XAML 頁面之間巡覽時的物件：

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

## <a name="ctor"></a>  Object:: object 建構函式

初始化 Object 類別的新執行個體。

### <a name="syntax"></a>語法

```cpp
public:Object();
```

## <a name="referenceequals"></a>  Object:: referenceequals 方法

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

**true**兩個物件是否相同，否則**false**。

## <a name="tostring"></a>  Object:: tostring 方法 (C + + /CX)

傳回代表目前物件的字串。

### <a name="syntax"></a>語法

```cpp
public:
virtual String^ ToString();
```

### <a name="return-value"></a>傳回值

表示目前物件的字串。 您可以在 ref 類別或結構中覆寫這個方法，提供自訂字串訊息：

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
