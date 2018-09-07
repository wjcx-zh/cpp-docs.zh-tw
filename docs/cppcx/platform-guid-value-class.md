---
title: 'Platform:: guid 實值類別 |Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
dev_langs:
- C++
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e115cf74eaac194c9e5b7154898cc23e10b220eb
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100427"
---
# <a name="platformguid-value-class"></a>Platform::Guid 實值類別

代表[GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931\(v=vs.85\).aspx) Windows 執行階段型別系統中的型別。

## <a name="syntax"></a>語法

```cpp
public value struct Guid
```

### <a name="members"></a>成員

GUID 具有 Equals()、GetHashCode() 和 ToString() 方法 (衍生自 [Platform::Object Class](../cppcx/platform-object-class.md))，以及 GetTypeCode() 方法 (衍生自 [Platform::Type Class](../cppcx/platform-type-class.md). Guid 也具有下列成員。

|成員|描述|
|------------|-----------------|
|[Guid](#ctor)|初始化 Guid 結構的新執行個體。|
|[operator==](#operator-equality)|等於運算子。|
|[operator!=](#operator-not-equal)|不等於運算子。|
|[operator()](#operator-call)|將 Guid 轉換成 GUID。|

### <a name="remarks"></a>備註

如需如何產生新 platform:: guid 使用 Windows 函式的範例[CoCreateGuid](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateguid)，請參閱[WinRT 元件： 如何產生 GUID？](http://blogs.msdn.com/b/eternalcoding/archive/2013/03/25/winrt-component-how-to-generate-a-guid.aspx)

### <a name="requirements"></a>需求

**最低支援用戶端：** Windows 8

**最低支援伺服器：** Windows Server 2012

**命名空間：** Platform

**中繼資料：** platform.winmd

## <a name="ctor"></a> Guid:: guid 建構函式

初始化 Guid 結構的新執行個體。

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
GUID 的前 4 個位元組。

*b*<br/>
GUID 接下來的 2 個位元組。

*C*<br/>
GUID 接下來的 2 個位元組。

*d*<br/>
GUID 的下一個位元組。

*e*<br/>
GUID 的下一個位元組。

*f*<br/>
GUID 的下一個位元組。

*g*<br/>
GUID 的下一個位元組。

*h*<br/>
GUID 的下一個位元組。

*i*<br/>
GUID 的下一個位元組。

*j*<br/>
GUID 的下一個位元組。

*k*<br/>
GUID 的下一個位元組。

*m*<br/>
所定義的 GUID。

*n*<br/>
GUID 剩餘的 8 個位元組。

## <a name="operator-equality"></a> Guid::operator = = 運算子

比較兩個 guid。

### <a name="syntax"></a>語法

```cpp
Platform::Guid::operator==
```

### <a name="return-value"></a>傳回值

如果兩個 guid 相等，則為 true。

## <a name="operator-inequality"></a> Guid::operator ！ = 運算子

比較兩個 guid。

### <a name="syntax"></a>語法

```cpp
Platform::Guid::operator!=
```

### <a name="return-value"></a>傳回值

如果兩個 guid 是否不相等，則為 true。

## <a name="operator-call"></a> Guid::operator() 運算子

將隱含轉換[GUID 結構](https://msdn.microsoft.com/library/windows/desktop/aa373931\(v=vs.85\).aspx)platform:: GUID。

### <a name="syntax"></a>語法

```cpp
Platform::Guid operator();
```

### <a name="return-value"></a>傳回值

Guid 結構。

## <a name="see-also"></a>另請參閱

[Platform 命名空間](../cppcx/platform-namespace-c-cx.md)