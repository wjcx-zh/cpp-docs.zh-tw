---
title: "IAtlStringMgr 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAtlStringMgr
dev_langs:
- C++
helpviewer_keywords:
- shared classes, IAtlStringMgr
- memory, managing
- IAtlStringMgr class
ms.assetid: 722f0346-a770-4aa7-8f94-177be8dba823
caps.latest.revision: 16
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
ms.openlocfilehash: 4ff4aa01a6d30f377560962f98a5892bdcc37837
ms.lasthandoff: 02/24/2017

---
# <a name="iatlstringmgr-class"></a>IAtlStringMgr 類別
此類別代表介面`CStringT`記憶體管理員。  
  
## <a name="syntax"></a>語法  
  
```
__interface IAtlStringMgr
```  
  
## <a name="members"></a>Members  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[配置](#allocate)|呼叫這個方法，以配置新的字串資料結構。|  
|[複製](#clone)|呼叫此方法以傳回新字串管理員用於另一個執行個體的指標`CSimpleStringT`。|  
|[免費](#free)|呼叫此方法以釋放字串資料結構。|  
|[GetNilString](#getnilstring)|傳回的指標`CStringData`空字串的物件所使用的物件。|  
|[重新配置](#reallocate)|呼叫這個方法來重新配置的字串資料結構。|  
  
## <a name="remarks"></a>備註  
 這個介面會獨立於 MFC 字串類別中，所使用的記憶體管理例如[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)， [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)，和[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)。  
  
 您也可以使用這個類別來實作自訂記憶體管理員為您的自訂字串類別。 如需詳細資訊，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlsimpstr.h  
  
##  <a name="a-nameallocatea--iatlstringmgrallocate"></a><a name="allocate"></a>IAtlStringMgr::Allocate  
 會配置新的字串資料結構。  
  
```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```  
  
### <a name="parameters"></a>參數  
 `nAllocLength`  
 新的記憶體區塊中的字元數。  
  
 `nCharSize`  
 字串管理員所使用的字元類型的大小 （以位元組為單位）。  
  
### <a name="return-value"></a>傳回值  
 傳回新配置記憶體區塊的指標。  
  
> [!NOTE]
>  發出的訊號失敗的配置，而擲回例外狀況。 相反地，失敗的配置應該藉由傳回信號**NULL**。  
  
### <a name="remarks"></a>備註  
 呼叫[IAtlStringMgr::Free](#free)或[IAtlStringMgr::ReAllocate](#reallocate)釋放透過這個方法配置的記憶體。  
  
> [!NOTE]
>  使用方式範例，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
##  <a name="a-nameclonea--iatlstringmgrclone"></a><a name="clone"></a>IAtlStringMgr::Clone  
 傳回新字串管理員用於另一個執行個體的指標`CSimpleStringT`。  
  
```
IAtlStringMgr* Clone() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回一份`IAtlStringMgr`物件。  
  
### <a name="remarks"></a>備註  
 字串管理員需要為新的字串時，通常稱為架構。 在大部分情況下，**這**會傳回的指標。  
  
 不過，如果記憶體管理員不支援使用多個執行個體`CSimpleStringT`，應該會傳回共用字串管理員的指標。  
  
> [!NOTE]
>  使用方式範例，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
##  <a name="a-namefreea--iatlstringmgrfree"></a><a name="free"></a>IAtlStringMgr::Free  
 釋出的字串資料結構。  
  
```
void Free(CStringData* pData) throw();
```  
  
### <a name="parameters"></a>參數  
 `pData`  
 要釋放的記憶體區塊指標。  
  
### <a name="remarks"></a>備註  
 釋放先前配置所指定的記憶體區塊[配置](#allocate)或[重新配置](../../atl/reference/iatlmemmgr-class.md#reallocate)。  
  
> [!NOTE]
>  使用方式範例，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
##  <a name="a-namegetnilstringa--iatlstringmgrgetnilstring"></a><a name="getnilstring"></a>IAtlStringMgr::GetNilString  
 傳回空字串的字串資料結構的指標。  
  
```
CStringData* GetNilString() throw();
```  
  
### <a name="return-value"></a>傳回值  
 指標`CStringData`物件用來表示空字串。  
  
### <a name="remarks"></a>備註  
 呼叫此函式傳回空的字串表示法。  
  
> [!NOTE]
>  在實作自訂字串管理員時，此函式必須永遠不會失敗。 您可以內嵌的執行個體來確定這**CNilStringData**字串管理員類別，並傳回指標，該執行個體中。  
  
> [!NOTE]
>  使用方式範例，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
##  <a name="a-namereallocatea--iatlstringmgrreallocate"></a><a name="reallocate"></a>IAtlStringMgr::Reallocate  
 重新配置的字串資料結構。  
  
```
CStringData* Reallocate(  
 CStringData* pData,
 int nAllocLength,
 int nCharSize) throw();
```  
  
### <a name="parameters"></a>參數  
 `pData`  
 此記憶體管理員先前配置的記憶體指標。  
  
 `nAllocLength`  
 新的記憶體區塊中的字元數。  
  
 `nCharSize`  
 字串管理員所使用的字元類型的大小 （以位元組為單位）。  
  
### <a name="return-value"></a>傳回值  
 傳回新配置記憶體區塊開頭的指標。  
  
### <a name="remarks"></a>備註  
 呼叫此函式，若要調整現有所指定的記憶體區塊`pData`。  
  
 呼叫[IAtlStringMgr::Free](#free)釋放透過這個方法配置的記憶體。  
  
> [!NOTE]
>  使用方式範例，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)



