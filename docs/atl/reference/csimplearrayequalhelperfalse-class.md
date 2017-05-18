---
title: "CSimpleArrayEqualHelperFalse 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: cd5ed7058194880ef1ceaebe788e3deb60d4ac8e
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

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
  
|名稱|描述|  
|----------|-----------------|  
|[CSimpleArrayEqualHelperFalse::IsEqual](#isequal)|（靜態）傳回 false。|  
  
## <a name="remarks"></a>備註  
 此特性類別是一個補充`CSimpleArray`類別。 It 一律傳回 false，然後另外將呼叫`ATLASSERT`是 false，如果曾被參考的引數。 在等號比較測試未充分定義所在的情況下，這個類別可讓陣列，其中包含大部分方法正確運作，但在定義完善的方式，例如視比較的方法失敗的項目[CSimpleArray::Find](../../atl/reference/csimplearray-class.md#find)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlsimpcoll.h  
  
##  <a name="isequal"></a>CSimpleArrayEqualHelperFalse::IsEqual  
 傳回 false。  
  
```
static bool IsEqual(const T&, const T&);
```  
  
### <a name="return-value"></a>傳回值  
 傳回 false。  
  
### <a name="remarks"></a>備註  
 這個方法一律傳回 false，並將呼叫`ATLASSERT`是 false，如果參考的引數。 目的`CSimpleArrayEqualHelperFalse::IsEqual`是強制使用等號比較測試沒有充分定義完善的方式失敗的比較方法。  
  
## <a name="see-also"></a>另請參閱  
 [CSimpleArrayEqualHelper 類別](../../atl/reference/csimplearrayequalhelper-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

