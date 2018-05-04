---
title: CComHeapPtr 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComHeapPtr
- ATLBASE/ATL::CComHeapPtr
- ATLBASE/ATL::CComHeapPtr::CComHeapPtr
dev_langs:
- C++
helpviewer_keywords:
- CComHeapPtr class
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1937bb96cabfd1a42650e2a27fd04c11aa648f2b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
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
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComHeapPtr::CComHeapPtr](#ccomheapptr)|建構函式。|  
  
## <a name="remarks"></a>備註  
 `CComHeapPtr` 衍生自`CHeapPtr`，但是會使用[CComAllocator](../../atl/reference/ccomallocator-class.md)配置的記憶體使用 COM 常式。 請參閱[CHeapPtr](../../atl/reference/cheapptr-class.md)和[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)可用的方法。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)  
  
 [CHeapPtr](../../atl/reference/cheapptr-class.md)  
  
 `CComHeapPtr`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
##  <a name="ccomheapptr"></a>  CComHeapPtr::CComHeapPtr  
 建構函式。  
  
```
CComHeapPtr() throw();
explicit CComHeapPtr(T* pData) throw();
```  
  
### <a name="parameters"></a>參數  
 `pData`  
 現有的 `CComHeapPtr` 物件。  
  
### <a name="remarks"></a>備註  
 堆積指標可以選擇性地建立使用現有`CComHeapPtr`物件。 如果是的話，新`CComHeapPtr`物件負責管理新的指標和資源。  
  
## <a name="see-also"></a>另請參閱  
 [CHeapPtr 類別](../../atl/reference/cheapptr-class.md)   
 [CHeapPtrBase 類別](../../atl/reference/cheapptrbase-class.md)   
 [CComAllocator 類別](../../atl/reference/ccomallocator-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
