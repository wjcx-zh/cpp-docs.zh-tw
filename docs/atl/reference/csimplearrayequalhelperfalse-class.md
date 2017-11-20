---
title: "CSimpleArrayEqualHelperFalse 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse::IsEqual
dev_langs: C++
helpviewer_keywords: CSimpleArrayEqualHelperFalse class
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b42c7717757d3648db368e7d9633162fa87afe9f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="csimplearrayequalhelperfalse-class"></a>CSimpleArrayEqualHelperFalse 類別
這個類別是 helper [CSimpleArray](../../atl/reference/csimplearray-class.md)類別。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>  
class CSimpleArrayEqualHelperFalse
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 在衍生的類別中。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CSimpleArrayEqualHelperFalse::IsEqual](#isequal)|（靜態）傳回 false。|  
  
## <a name="remarks"></a>備註  
 這個特性類別是一個補充`CSimpleArray`類別。 It 一律傳回 false，並另外，將會呼叫`ATLASSERT`false 曾經正在參考它的引數。 在等號比較測試未充分定義所在的情況下，這個類別可讓陣列，其中包含大部分方法正確運作，但以妥善定義的方式，例如視比較的方法失敗的項目[CSimpleArray::尋找](../../atl/reference/csimplearray-class.md#find)。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlsimpcoll.h  
  
##  <a name="isequal"></a>CSimpleArrayEqualHelperFalse::IsEqual  
 傳回 false。  
  
```
static bool IsEqual(const T&, const T&);
```  
  
### <a name="return-value"></a>傳回值  
 傳回 false。  
  
### <a name="remarks"></a>備註  
 這個方法一律會傳回 false，並將呼叫`ATLASSERT`是 false，如果參考的引數。 目的`CSimpleArrayEqualHelperFalse::IsEqual`是強制方法使用的比較時沒有充分定義等號比較測試，以妥善定義的方式失敗。  
  
## <a name="see-also"></a>另請參閱  
 [CSimpleArrayEqualHelper 類別](../../atl/reference/csimplearrayequalhelper-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
