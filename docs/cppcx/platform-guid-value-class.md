---
title: Platform::Guid 實值類別
ms.date: 01/15/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: f63b2bb4fd5f809861622a4f6b255ee3725564b6
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816584"
---
# <a name="platformguid-value-class"></a>Platform::Guid 實值類別

代表 Windows 執行階段類型系統中的 [GUID](/previous-versions/cc317743(v%3dmsdn.10)) 類型。

## <a name="syntax"></a>語法

```cpp
public value struct Guid
```

### <a name="members"></a>Members

`Platform::Guid` 具有衍生自[platform：： Object 類別](../cppcx/platform-object-class.md)的 `Equals()`、`GetHashCode()`和 `ToString()` 方法，以及衍生自[Platform：： Type 類別](../cppcx/platform-type-class.md)的 `GetTypeCode()` 方法。 `Platform::Guid` 也具有下列成員。

|成員|描述|
|------------|-----------------|
|[Guid](#ctor)|初始化 `Platform::Guid` 的新執行個體。|
|[operator==](#operator-equality)|等於運算子。|
|[operator!=](#operator-inequality)|不等於運算子。|
|[operator&lt;](#operator-less)|小於運算子。|
|[operator()](#operator-call)|將 `Platform::Guid` 轉換成 `GUID`。|

### <a name="remarks"></a>備註

若要產生新的 `Platform::Guid`，請使用[Windows：： Foundation：： GuidHelper：： CreateNewGuid](/uwp/api/windows.foundation.guidhelper.createnewguid#Windows_Foundation_GuidHelper_CreateNewGuid)靜態方法。

### <a name="requirements"></a>需求

**最低支援用戶端：** Windows 8

**最低支援伺服器：** Windows Server 2012

**命名空間：** Platform

**中繼資料：** platform.winmd

## <a name="ctor"></a>Guid：： Guid 構造函式

初始化 `Platform::Guid` 的新執行個體。

### <a name="syntax"></a>語法

```cpp
Guid(
    unsigned int a,
    unsigned short b,
    unsigned short c,
    unsigned char d,
    unsigned char e,
    unsigned char f,
    unsigned char g,
    unsigned char h,
    unsigned char i,
    unsigned char j,
    unsigned char k );

Guid(GUID m);

Guid(
    unsigned int a,
    unsigned short b,
    unsigned short c,
    Array<unsigned char>^ n );
```

### <a name="parameters"></a>參數

*a*<br/>
`GUID`的前4個位元組。

*b*<br/>
`GUID`的後2個位元組。

*C*<br/>
`GUID`的後2個位元組。

*d*<br/>
`GUID`的下一個位元組。

*e*<br/>
`GUID`的下一個位元組。

*f*<br/>
`GUID`的下一個位元組。

*g*<br/>
`GUID`的下一個位元組。

*h*<br/>
`GUID`的下一個位元組。

*i*<br/>
`GUID`的下一個位元組。

*韓文*<br/>
`GUID`的下一個位元組。

*k*<br/>
`GUID`的下一個位元組。

*m*<br/>
中的 `GUID`，其格式為[GUID 結構](/previous-versions/cc317743(v%3dmsdn.10))。

*n*<br/>
`GUID`剩餘的8個位元組。

## <a name="operator-equality"></a>Guid：： operator = = 運算子

比較兩個 `Platform::Guid` 執行個體是否相等。

### <a name="syntax"></a>語法

```cpp
static bool Platform::Guid::operator==(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>參數

*guid1*<br/>
要比較的第一個 `Platform::Guid`。

*guid2*<br/>
要比較的第二個 `Platform::Guid`。

### <a name="return-value"></a>傳回值

如果兩個 `Platform::Guid` 實例相等，則為 True。

### <a name="remarks"></a>備註

偏好使用 `==` 運算子，而不是[Windows：： Foundation：： GuidHelper：： Equals](/uwp/api/windows.foundation.guidhelper.equals)靜態方法。

## <a name="operator-inequality"></a>Guid：： operator！ = 運算子

比較兩個 `Platform::Guid` 實例是否不相等。

### <a name="syntax"></a>語法

```cpp
static bool Platform::Guid::operator!=(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>參數

*guid1*<br/>
要比較的第一個 `Platform::Guid`。

*guid2*<br/>
要比較的第二個 `Platform::Guid`。

### <a name="return-value"></a>傳回值

如果兩個 `Platform::Guid` 實例不相等，則為 True。

## <a name="operator-less"></a>Guid：： operator&lt; 運算子

比較兩個 `Platform::Guid` 實例以進行排序。

### <a name="syntax"></a>語法

```cpp
static bool Platform::Guid::operator<(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>參數

*guid1*<br/>
要比較的第一個 `Platform::Guid`。

*guid2*<br/>
要比較的第二個 `Platform::Guid`。

### <a name="return-value"></a>傳回值

如果*guid1*在*guid2*之前排序，則為 True。 排序會在將每個 `Platform::Guid` 視為 4 32 位不帶正負號值的陣列之後詞典編纂。 這不是 SQL Server 或 .NET Framework 所使用的順序，也不是依字串表示以字典順序排序。

提供這個運算子的目的，是為了讓C++標準程式庫可以更輕鬆地使用 `Guid` 物件。

## <a name="operator-call"></a>Guid：： operator （）運算子

隱含地將 `Platform::Guid` 轉換為[GUID 結構](/previous-versions/cc317743(v%3dmsdn.10))。

### <a name="syntax"></a>語法

```cpp
const GUID& Platform::Guid::operator();
```

### <a name="return-value"></a>傳回值

[GUID 結構](/previous-versions/cc317743(v%3dmsdn.10))。

## <a name="see-also"></a>另請參閱

[平台命名空間](../cppcx/platform-namespace-c-cx.md)
