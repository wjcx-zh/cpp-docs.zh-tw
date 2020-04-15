---
title: CDefault字元類別
ms.date: 11/04/2016
f1_keywords:
- CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits::CharToLower
- ATLCOLL/ATL::CDefaultCharTraits::CharToUpper
helpviewer_keywords:
- CDefaultCharTraits class
ms.assetid: f94a3934-597f-401d-8513-ed6924ae069a
ms.openlocfilehash: 40c4d107d05e6d7b610e7c46be920d91d8fe6086
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327098"
---
# <a name="cdefaultchartraits-class"></a>CDefault字元類別

此類提供兩個靜態函數,用於大寫大寫和大寫之間的字元轉換。

## <a name="syntax"></a>語法

```
template <typename T>
class CDefaultCharTraits
```

#### <a name="parameters"></a>參數

*T*<br/>
要存儲在集合中的數據類型。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Cdefault 字元::字元](#chartolower)|(靜態)呼叫此函數以將字元轉換為大寫。|
|[Cdefault 字元::字元上部](#chartoupper)|(靜態)呼叫此函數以將字元轉換為小寫。|

## <a name="remarks"></a>備註

此類提供類[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)使用的函數。

## <a name="requirements"></a>需求

**標題:** atlcoll.h

## <a name="cdefaultchartraitschartolower"></a><a name="chartolower"></a>Cdefault 字元::字元

呼叫此函數以將字元轉換為小寫。

```
static wchar_t CharToLower(wchar_t x);
static char CharToLower(char x);
```

### <a name="parameters"></a>參數

*X.*<br/>
要轉換為小寫的字元。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#132](../../atl/codesnippet/cpp/cdefaultchartraits-class_1.cpp)]

## <a name="cdefaultchartraitschartoupper"></a><a name="chartoupper"></a>Cdefault 字元::字元上部

呼叫此函數以將字元轉換為大寫。

```
static wchar_t CharToUpper(wchar_t x);
static char CharToUpper(char x);
```

### <a name="parameters"></a>參數

*X.*<br/>
要轉換為大寫的字元。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
