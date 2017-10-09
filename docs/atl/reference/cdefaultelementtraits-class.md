---
title: "CDefaultElementTraits 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDefaultElementTraits
- atlcoll/ATL::CDefaultElementTraits
dev_langs:
- C++
helpviewer_keywords:
- CDefaultElementTraits class
ms.assetid: ac5ee610-7957-4b7c-92b6-38ff72e4118e
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: c55726a1728185f699afbac4ba68a6dc0f70c2bf
ms.openlocfilehash: 1ddb59d2ac448725de719423d1634f00e568d2c9
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="cdefaultelementtraits-class"></a>CDefaultElementTraits 類別
這個類別會提供預設的方法和函式集合類別。  
  
## <a name="syntax"></a>語法  
  
```
template <typename T>  
class CDefaultElementTraits : public CElementTraitsBase<T>,
    public CDefaultHashTraits<T>,
    public CDefaultCompareTraits<T>
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 若要儲存在集合中的資料類型。  
  
## <a name="remarks"></a>備註  
 這個類別會提供預設靜態函式和方法，移動、 複製、 比較和集合類別物件中儲存的雜湊項目。 此類別衍生其函式和方法，從[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)， [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)，和[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)，並使用[CElementTraits](../../atl/reference/celementtraits-class.md)， [CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)，和[CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md)。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcoll.h  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

