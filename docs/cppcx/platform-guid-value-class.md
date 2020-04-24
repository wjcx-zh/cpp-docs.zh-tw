---
title: Platform::Guid 實值類別
ms.date: 01/15/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: 7c3b89ff238b1cb5ee9fbb71e83d20f571e656a3
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82031533"
---
# <a name="platformguid-value-class"></a>Platform::Guid 實值類別

表示 Windows 執行時類型系統中的 [GUID](/視窗/win32/api/guiddef/ns-guiddef-guid-guid 類型)。

## <a name="syntax"></a>語法

```cpp
public value struct Guid
```

### <a name="members"></a>成員

`Platform::Guid`[Platform::Type Class](../cppcx/platform-type-class.md)`Equals()`具有 派生自平臺:物件類的方法,以及從平臺派生的方法::類型類 。 `GetHashCode()` `ToString()` [ ](../cppcx/platform-object-class.md) `GetTypeCode()` `Platform::Guid`也有以下成員。

|member|描述|
|------------|-----------------|
|[Guid](#ctor)|初始化 `Platform::Guid` 的新執行個體。|
|[運算子*](#operator-equality)|等於運算子。|
|[操作員!](#operator-inequality)|不等於運算子。|
|[算子&lt;](#operator-less)|小於運算子。|
|[運算子()](#operator-call)|將 `Platform::Guid` 轉換成 `GUID`。|

### <a name="remarks"></a>備註

要生成新`Platform::Guid`,請使用[Windows::基礎::GuidHelper::創建新 Guid](/uwp/api/windows.foundation.guidhelper.createnewguid)靜態方法。

### <a name="requirements"></a>需求

**受支援的最小用戶端:** 視窗 8

**受支援的伺服器最少:** 視窗伺服器 2012

**命名空間：** Platform

**中繼資料：** platform.winmd

## <a name="guidguid-constructors"></a><a name="ctor"></a>吉德::吉德構造函數

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
的前 4`GUID`個字節 。

*B*<br/>
的下 2 個字`GUID`節。

*C*<br/>
的下 2 個字`GUID`節。

*d*<br/>
`GUID` 的下一個位元組。

*e*<br/>
`GUID` 的下一個位元組。

*F*<br/>
`GUID` 的下一個位元組。

*G*<br/>
`GUID` 的下一個位元組。

*H*<br/>
`GUID` 的下一個位元組。

*I.*<br/>
`GUID` 的下一個位元組。

*J*<br/>
`GUID` 的下一個位元組。

*K*<br/>
`GUID` 的下一個位元組。

*米*<br/>
A`GUID`形式為[GUID 結構](/windows/win32/api/guiddef/ns-guiddef-guid)。

*n*<br/>
其餘 8 個字`GUID`節的 。

## <a name="guidoperator-operator"></a><a name="operator-equality"></a>吉德:::操作員=運算符

比較兩個 `Platform::Guid` 執行個體是否相等。

### <a name="syntax"></a>語法

```cpp
static bool Platform::Guid::operator==(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>參數

*吉德1*<br/>
要比較的第一個 `Platform::Guid`。

*吉德2*<br/>
要比較的第二個 `Platform::Guid`。

### <a name="return-value"></a>傳回值

如果兩`Platform::Guid`個實例相等,則為 True。

### <a name="remarks"></a>備註

更喜歡使用`==`運算符而不是[Windows:基礎::GuidHelper::等於](/uwp/api/windows.foundation.guidhelper.equals)靜態方法。

## <a name="guidoperator-operator"></a><a name="operator-inequality"></a>吉德::操作員!

比較兩個 `Platform::Guid` 執行個體是否不相等。

### <a name="syntax"></a>語法

```cpp
static bool Platform::Guid::operator!=(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>參數

*吉德1*<br/>
要比較的第一個 `Platform::Guid`。

*吉德2*<br/>
要比較的第二個 `Platform::Guid`。

### <a name="return-value"></a>傳回值

如果兩`Platform::Guid`個實例不相等,則為 True。

## <a name="guidoperatorlt-operator"></a><a name="operator-less"></a>吉德::操作員&lt;

比較兩`Platform::Guid`個排序實例。

### <a name="syntax"></a>語法

```cpp
static bool Platform::Guid::operator<(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>參數

*吉德1*<br/>
要比較的第一個 `Platform::Guid`。

*吉德2*<br/>
要比較的第二個 `Platform::Guid`。

### <a name="return-value"></a>傳回值

如果*guid1*是在*guid2*之前訂購的,則為 True。 排序是字典,在將每個`Platform::Guid`值視為四個 32 位無符號值的陣列。 這不是 SQL Server 或 .NET 框架使用的順序,也不與字串表示法的字典排序相同。

提供此運算符,以便`Guid`C++標準庫可以更輕鬆地使用物件。

## <a name="guidoperator-operator"></a><a name="operator-call"></a>吉德::管理員() 運算子

隱含轉換`Platform::Guid`為[GUID 結構](/windows/win32/api/guiddef/ns-guiddef-guid)。

### <a name="syntax"></a>語法

```cpp
const GUID& Platform::Guid::operator();
```

### <a name="return-value"></a>傳回值

[GUID 結構](/windows/win32/api/guiddef/ns-guiddef-guid)。

## <a name="see-also"></a>另請參閱

[平台命名空間](../cppcx/platform-namespace-c-cx.md)
