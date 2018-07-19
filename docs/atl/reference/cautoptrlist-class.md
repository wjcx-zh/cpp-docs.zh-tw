---
title: CAutoPtrList 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList::CAutoPtrList
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtrList class
ms.assetid: 11de4aca-28b0-4ff2-a74a-cb602312ffbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5d942c0611b408303922f3e6ab91000630ce8774
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883589"
---
# <a name="cautoptrlist-class"></a>CAutoPtrList 類別
建構的智慧型指標清單時，這個類別會提供有用的方法。  
  
> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template<typename E>  
class CAutoPtrList : 
   public CAtlList<ATL::CAutoPtr<E>, CAutoPtrElementTraits<E>>
```  
  
#### <a name="parameters"></a>參數  
 *E*  
 指標類型。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAutoPtrList::CAutoPtrList](#cautoptrlist)|建構函式。|  
  
## <a name="remarks"></a>備註  
 這個類別提供建構函式，並衍生方法從[CAtlList](../../atl/reference/catllist-class.md)並[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)來協助建立儲存智慧型指標的清單物件。 此類別[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)的陣列物件提供類似的函式。  
  
 如需詳細資訊，請參閱 < [ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CAutoPtrList`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcoll.h  
  
##  <a name="cautoptrlist"></a>  CAutoPtrList::CAutoPtrList  
 建構函式。  
  
```
CAutoPtrList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>參數  
 *nBlockSize*  
 區塊的大小，預設值是 10。  
  
### <a name="remarks"></a>備註  
 區塊大小是記憶體的配置新的項目時所需數量的量值。 較大的區塊大小會減少記憶體配置常式，呼叫，但使用較多資源。  
  
## <a name="see-also"></a>另請參閱  
 [CAtlList 類別](../../atl/reference/catllist-class.md)   
 [CAutoPtrElementTraits 類別](../../atl/reference/cautoptrelementtraits-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
