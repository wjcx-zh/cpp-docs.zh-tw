---
title: "CAutoPtrArray 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
dev_langs: C++
helpviewer_keywords: CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 952f6a6d9fa06c0f0c34e5769b4302c6230abb43
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="cautoptrarray-class"></a>CAutoPtrArray 類別
建構智慧型指標的陣列時，這個類別會提供有用的方法。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <typename E>
class CAutoPtrArray : public CAtlArray<
                        ATL::CAutoPtr<E>,
                        CAutoPtrElementTraits<E>>
```  
  
#### <a name="parameters"></a>參數  
 `E`  
 指標類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CAutoPtrArray::CAutoPtrArray](#cautoptrarray)|建構函式。|  
  
## <a name="remarks"></a>備註  
 這個類別提供建構函式，並衍生方法[CAtlArray](../../atl/reference/catlarray-class.md)和[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)協助儲存智慧型指標集合類別物件的建立。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CAtlArray`  
  
 `CAutoPtrArray`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcoll.h  
  
##  <a name="cautoptrarray"></a>CAutoPtrArray::CAutoPtrArray  
 建構函式。  
  
```
CAutoPtrArray() throw();
```  
  
### <a name="remarks"></a>備註  
 初始化智慧型指標陣列。  
  
## <a name="see-also"></a>另請參閱  
 [CAtlArray 類別](../../atl/reference/catlarray-class.md)   
 [CAutoPtrElementTraits 類別](../../atl/reference/cautoptrelementtraits-class.md)   
 [CAutoPtrList 類別](../../atl/reference/cautoptrlist-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
