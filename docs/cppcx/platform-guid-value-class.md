---
title: Platform::Guid 實值類別
ms.date: 01/15/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: 8d6c71028e4f93064c7b4df978678b5f7c26d6bc
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504524"
---
# <a name="platformguid-value-class"></a>Platform::Guid 實值類別

代表 Windows 執行階段類型系統中的 [GUID](/previous-versions/aa373931\(v=vs.80\)) 類型。

## <a name="syntax"></a>語法

```cpp
public value struct Guid
```

### <a name="members"></a>成員

`Platform::Guid` 已`Equals()`， `GetHashCode()`，並`ToString()`方法衍生自[platform:: object 類別](../cppcx/platform-object-class.md)，而`GetTypeCode()`方法衍生自[platform:: type 類別](../cppcx/platform-type-class.md)。 `Platform::Guid` 也具有下列成員。

|成員|描述|
|------------|-----------------|
|[Guid](#ctor)|初始化 `Platform::Guid` 的新執行個體。|
|[operator==](#operator-equality)|等於運算子。|
|[operator!=](#operator-inequality)|不等於運算子。|
|[operator&lt;](#operator-less)|Less than 運算子。|
|[operator()](#operator-call)|將 `Platform::Guid` 轉換成 `GUID`。|

### <a name="remarks"></a>備註

若要產生新`Platform::Guid`，使用[Windows::Foundation::GuidHelper::CreateNewGuid](/uwp/api/windows.foundation.guidhelper.createnewguid#Windows_Foundation_GuidHelper_CreateNewGuid)靜態方法。

### <a name="requirements"></a>需求

**最低支援用戶端：** Windows 8

**最低支援伺服器：** Windows Server 2012

**命名空間：** Platform

**中繼資料：** platform.winmd

## <a name="ctor"></a> Guid:: guid 建構函式

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
前 4 個位元組`GUID`。

*b*<br/>
接下來的 2 個位元組的`GUID`。

*C*<br/>
接下來的 2 個位元組的`GUID`。

*d*<br/>
下一個位元組`GUID`。

*e*<br/>
下一個位元組`GUID`。

*f*<br/>
下一個位元組`GUID`。

*g*<br/>
下一個位元組`GUID`。

*h*<br/>
下一個位元組`GUID`。

*i*<br/>
下一個位元組`GUID`。

*j*<br/>
下一個位元組`GUID`。

*k*<br/>
下一個位元組`GUID`。

*m*<br/>
A`GUID`形式[GUID 結構](/previous-versions/aa373931\(v=vs.80\))。

*n*<br/>
剩餘的 8 個位元組`GUID`。

## <a name="operator-equality"></a> Guid::operator = = 運算子

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

如果兩個`Platform::Guid`執行個體是否相等。

### <a name="remarks"></a>備註

偏好使用`==`運算子來取代[Windows::Foundation::GuidHelper::Equals](/uwp/api/windows.foundation.guidhelper.equals)靜態方法。

## <a name="operator-inequality"></a> Guid::operator ！ = 運算子

比較兩個`Platform::Guid`執行個體是否不相等。

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

如果兩個`Platform::Guid`執行個體不相等。

## <a name="operator-less"></a> Guid::operator&lt;運算子

比較兩個`Platform::Guid`排序的執行個體。

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

則為 true *guid1*排序之前*guid2*。 排序是之後將每個字典編撰`Platform::Guid`好像是四個 32 位元不帶正負號值的陣列。 這不是 SQL Server 或.NET Framework 中，所使用的順序，也不是由字串表示詞彙編纂順序相同。

這個運算子會提供以便`Guid`物件可以由更輕鬆地取用C++標準程式庫。

## <a name="operator-call"></a> Guid::operator() 運算子

將隱含轉換`Platform::Guid`要[GUID 結構](/previous-versions/aa373931\(v=vs.80\))。

### <a name="syntax"></a>語法

```cpp
const GUID& Platform::Guid::operator();
```

### <a name="return-value"></a>傳回值

A [GUID 結構](/previous-versions/aa373931\(v=vs.80\))。

## <a name="see-also"></a>另請參閱

[平台命名空間](../cppcx/platform-namespace-c-cx.md)
