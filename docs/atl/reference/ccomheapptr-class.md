---
title: "CComHeapPtr 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CComHeapPtr
- ATL.CComHeapPtr<T>
- ATL::CComHeapPtr<T>
- CComHeapPtr
- ATL.CComHeapPtr
dev_langs:
- C++
helpviewer_keywords:
- CComHeapPtr class
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
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
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 0e5196a98b8fd76b2e7e791fd2cd9549099a1cc9
ms.lasthandoff: 02/24/2017

---
# <a name="ccomheapptr-class"></a>CComHeapPtr 類別
用來管理堆積指標的智慧型指標類別。  
  
## <a name="syntax"></a>語法  
  
```
template<typename T>  
class CComHeapPtr : public CHeapPtr<T, CComAllocator>
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 要儲存在堆積上的物件類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CComHeapPtr::CComHeapPtr](#ccomheapptr)|建構函式。|  
  
## <a name="remarks"></a>備註  
 `CComHeapPtr`衍生自`CHeapPtr`，但使用[CComAllocator](../../atl/reference/ccomallocator-class.md)配置的記憶體使用 COM 常式。 請參閱[CHeapPtr](../../atl/reference/cheapptr-class.md)和[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)可用的方法。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)  
  
 [CHeapPtr](../../atl/reference/cheapptr-class.md)  
  
 `CComHeapPtr`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
##  <a name="a-nameccomheapptra--ccomheapptrccomheapptr"></a><a name="ccomheapptr"></a>CComHeapPtr::CComHeapPtr  
 建構函式。  
  
```
CComHeapPtr() throw();
explicit CComHeapPtr(T* pData) throw();
```  
  
### <a name="parameters"></a>參數  
 `pData`  
 現有的 `CComHeapPtr` 物件。  
  
### <a name="remarks"></a>備註  
 堆積的指標可以選擇性地建立使用現有`CComHeapPtr`物件。 如果是的話，新`CComHeapPtr`物件負責管理新的指標和資源。  
  
## <a name="see-also"></a>另請參閱  
 [CHeapPtr 類別](../../atl/reference/cheapptr-class.md)   
 [CHeapPtrBase 類別](../../atl/reference/cheapptrbase-class.md)   
 [CComAllocator 類別](../../atl/reference/ccomallocator-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

