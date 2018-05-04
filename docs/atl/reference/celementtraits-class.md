---
title: CElementTraits 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CElementTraits
- atlcoll/ATL::CElementTraits
dev_langs:
- C++
helpviewer_keywords:
- CElementTraits class
ms.assetid: 496528e5-7f80-4b45-be0c-6f646feb43c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c530622f096ef14d4eb3de56e5219e8f7df4f082
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="celementtraits-class"></a>CElementTraits 類別
這個類別的集合類別用於提供方法和函式移動、 複製、 比較和雜湊作業。  
  
## <a name="syntax"></a>語法  
  
```
template<typename T>  
class CElementTraits : public CDefaultElementTraits<T>
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 若要儲存在集合中的資料類型。  
  
## <a name="remarks"></a>備註  
 這個類別會提供預設靜態函式和方法，移動、 複製、 比較和集合類別物件中儲存的雜湊項目。 `CElementTraits` 指定為預設提供者，這些作業的集合類別[CAtlArray](../../atl/reference/catlarray-class.md)， [CAtlList](../../atl/reference/catllist-class.md)， [CRBMap](../../atl/reference/crbmap-class.md)， [CRBMultiMap](../../atl/reference/crbmultimap-class.md)，和[CRBTree](../../atl/reference/crbtree-class.md)。  
  
 預設實作都可以使用簡單的資料類型，但集合類別用來儲存更為複雜的物件，如果函式和方法必須覆寫使用者所提供的實作。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcoll.h  
  
## <a name="see-also"></a>另請參閱  
 [CDefaultElementTraits 類別](../../atl/reference/cdefaultelementtraits-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
