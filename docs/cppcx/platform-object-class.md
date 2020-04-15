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
ms.openlocfilehash: 8300ec484bdb58919ce8e450b706dd07c275ceee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363692"
---
# <a name="platformobject-class"></a>Platform::Object 類別

為 Windows 運行時應用中的 ref 類和引用結構提供常見行為。 所有 ref 類別和 ref 結構執行個體都會隱含轉換為 Platform::Object^，而且也都能覆寫其虛擬 ToString 方法。

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
|[Object::GetHashCode](#gethashcode)|傳回此執行個體的雜湊碼。|
|[Object::ReferenceEquals](#referenceequals)|判斷指定的物件執行個體是否為相同的執行個體。|
|[ToString](#tostring)|傳回代表目前物件的字串。 可以被覆寫。|
|[GetType](#gettype)|取得可描述目前執行個體的 [Platform::Type](../cppcx/platform-type-class.md) 。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`Object`

`Object`

### <a name="requirements"></a>需求

**標頭：** vccorlib.h

**命名空間：** Platform

## <a name="objectequals-method"></a><a name="equals"></a>物件:等於方法

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

如果物件相等,**則為 true,** 否則**為 false**。

## <a name="objectgethashcode-method"></a><a name="gethashcode"></a>對象:取得哈希碼方法

傳回這個執行個體的 `IUnknown`* 識別值 (如果它是 COM 物件)，或計算的雜湊值 (如果它不是 COM 物件)。

### <a name="syntax"></a>語法

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>傳回值

可唯一識別這個物件的數值。

### <a name="remarks"></a>備註

您可以使用 GetHashCode，在對應中建立物件的索引鍵。 您可以使用[Object::等於 來](#equals)比較哈希代碼。 如果程式碼路徑非常重要，而且 `GetHashCode` 和 `Equals` 不夠快，您可以下拉到基礎 COM 層，並且進行原生 `IUnknown` 指標比較。

## <a name="objectgettype-method"></a><a name="gettype"></a>物件:抓取類型方法

返回[一個平臺::鍵入](../cppcx/platform-type-class.md)描述對象的運行時類型的物件。

### <a name="syntax"></a>語法

```cpp
Object::GetType();
```

### <a name="property-valuereturn-value"></a>屬性值/傳回值

[平臺::鍵入](../cppcx/platform-type-class.md)描述對象的運行時類型的物件。

### <a name="remarks"></a>備註

靜態[類型::GetTypeCode](../cppcx/platform-type-class.md#gettypecode)可用於獲取表示當前類型的[平臺:typeCode 枚舉](../cppcx/platform-typecode-enumeration.md)值。 這對於內建類型而言非常有用。 除[Platform:String](../cppcx/platform-string-class.md)是物件 (1) 之外的任何 ref 類的類型代碼。

[Windows:UI:::Xaml:Interop::typeName](/uwp/api/windows.ui.xaml.interop.typename)類在 Windows API 中使用,作為在 Windows 元件和應用之間傳遞類型資訊的獨立於語言的方式。 T[平台:類型類](../cppcx/platform-type-class.md)具有用於`Type``TypeName`在和 之間轉換的運算符。

使用[typeid](../extensions/typeid-cpp-component-extensions.md)運算符傳`Platform::Type`回類別名稱的物件,例如在 XAML 頁之間導覽時:

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

## <a name="objectobject-constructor"></a><a name="ctor"></a>物件:物件建構函數

初始化 Object 類別的新執行個體。

### <a name="syntax"></a>語法

```cpp
public:Object();
```

## <a name="objectreferenceequals-method"></a><a name="referenceequals"></a>物件:參考相等方法

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

如果兩個物件相同,**則為 true;** 否則,**假**。

## <a name="objecttostring-method-ccx"></a><a name="tostring"></a>物件:到弦方法(C++/CX)

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

[平台命名空間](platform-namespace-c-cx.md)<br/>
[Platform::Type 類別](platform-type-class.md)<br/>
[型別系統](type-system-c-cx.md)
