---
title: CDefaultCharTraits 類別
ms.date: 11/04/2016
f1_keywords:
- CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits::CharToLower
- ATLCOLL/ATL::CDefaultCharTraits::CharToUpper
helpviewer_keywords:
- CDefaultCharTraits class
ms.assetid: f94a3934-597f-401d-8513-ed6924ae069a
ms.openlocfilehash: 8ea73da76f079359a4fc0250cacf70d10b545038
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660826"
---
# <a name="cdefaultchartraits-class"></a>CDefaultCharTraits 類別

這個類別提供兩個靜態函式之間大寫和小寫字元轉換。

## <a name="syntax"></a>語法

```
template <typename T>
class CDefaultCharTraits
```

#### <a name="parameters"></a>參數

*T*<br/>
若要在集合中儲存的資料型別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDefaultCharTraits::CharToLower](#chartolower)|（靜態）呼叫此函式可將字元轉換成大寫。|
|[CDefaultCharTraits::CharToUpper](#chartoupper)|（靜態）呼叫此函式可將字元轉換成小寫。|

## <a name="remarks"></a>備註

這個類別會提供函式所使用的類別[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)。

## <a name="requirements"></a>需求

**標頭：** atlcoll.h

##  <a name="chartolower"></a>  CDefaultCharTraits::CharToLower

呼叫此函式可將字元轉換成小寫。

```
static wchar_t CharToLower(wchar_t x);
static char CharToLower(char x);
```

### <a name="parameters"></a>參數

*x*<br/>
要轉換為小寫的字元。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#132](../../atl/codesnippet/cpp/cdefaultchartraits-class_1.cpp)]

##  <a name="chartoupper"></a>  CDefaultCharTraits::CharToUpper

呼叫此函式可將字元轉換成大寫。

```
static wchar_t CharToUpper(wchar_t x);
static char CharToUpper(char x);
```

### <a name="parameters"></a>參數

*x*<br/>
要轉換為大寫的字元。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
