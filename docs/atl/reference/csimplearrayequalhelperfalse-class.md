---
title: CSimpleArrayEqualHelperFalse 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse::IsEqual
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArrayEqualHelperFalse class
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74bc3326c50f1b460fc212074b7ca34dec518c76
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765631"
---
# <a name="csimplearrayequalhelperfalse-class"></a>CSimpleArrayEqualHelperFalse 類別

這個類別是 helper [CSimpleArray](../../atl/reference/csimplearray-class.md)類別。

## <a name="syntax"></a>語法

```
template <class T>  
class CSimpleArrayEqualHelperFalse
```

#### <a name="parameters"></a>參數

*T*  
在衍生的類別中。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSimpleArrayEqualHelperFalse::IsEqual](#isequal)|（靜態）會傳回 false。|

## <a name="remarks"></a>備註

此特性類別是一個補充`CSimpleArray`類別。 It 一律傳回 false，並另外，會呼叫`ATLASSERT`是 false，如果曾被參考的引數。 在等號比較測試不充分定義所在的情況下，這個類別可讓陣列，其中包含大部分方法的正確運作，但在定義完善的方式，例如取決於比較的方法中失敗的項目[CSimpleArray::尋找](../../atl/reference/csimplearray-class.md#find)。

## <a name="requirements"></a>需求

**標頭：** atlsimpcoll.h

##  <a name="isequal"></a>  CSimpleArrayEqualHelperFalse::IsEqual

傳回 false。

```
static bool IsEqual(const T&, const T&);
```

### <a name="return-value"></a>傳回值

傳回 false。

### <a name="remarks"></a>備註

這個方法一律會傳回 false，而且會呼叫`ATLASSERT`使用引數參考為 false。 目的`CSimpleArrayEqualHelperFalse::IsEqual`是強制方法使用時有充分定義等號比較測試，以定義完善的方式失敗的比較。

## <a name="see-also"></a>另請參閱

[CSimpleArrayEqualHelper 類別](../../atl/reference/csimplearrayequalhelper-class.md)   
[類別概觀](../../atl/atl-class-overview.md)
