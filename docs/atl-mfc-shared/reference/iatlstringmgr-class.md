---
title: IAtlStringMgr 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- IAtlStringMgr
- ATLSIMPSTR/ATL::IAtlStringMgr
- ATLSIMPSTR/ATL::Allocate
- ATLSIMPSTR/ATL::Clone
- ATLSIMPSTR/ATL::Free
- ATLSIMPSTR/ATL::GetNilString
- ATLSIMPSTR/ATL::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- shared classes, IAtlStringMgr
- memory, managing
- IAtlStringMgr class
ms.assetid: 722f0346-a770-4aa7-8f94-177be8dba823
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05d7ff0a38c0a557016887e6fce92fcb0bf28226
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="iatlstringmgr-class"></a>IAtlStringMgr 類別
此類別代表介面，以`CStringT`記憶體管理員。  
  
## <a name="syntax"></a>語法  
  
```
__interface IAtlStringMgr
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[配置](#allocate)|呼叫這個方法來配置新的字串資料結構。|  
|[複製](#clone)|呼叫此方法以傳回新字串管理員搭配另一個執行個體的指標`CSimpleStringT`。|  
|[可用](#free)|呼叫此方法以釋放字串資料結構。|  
|[GetNilString](#getnilstring)|將指標傳回至`CStringData`空字串的物件所使用的物件。|  
|[重新配置](#reallocate)|呼叫這個方法來重新配置的字串資料結構。|  
  
## <a name="remarks"></a>備註  
 這個介面可管理 MFC 無關的字串類別; 使用的記憶體例如[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)， [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)，和[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)。  
  
 您也可以使用這個類別來實作自訂的記憶體管理員為您的自訂字串類別。 如需詳細資訊，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlsimpstr.h  
  
##  <a name="allocate"></a>  IAtlStringMgr::Allocate  
 會配置新的字串資料結構。  
  
```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```  
  
### <a name="parameters"></a>參數  
 `nAllocLength`  
 在新的記憶體區塊中的字元數。  
  
 `nCharSize`  
 字串管理員所使用的字元類型的大小 （以位元組為單位）。  
  
### <a name="return-value"></a>傳回值  
 傳回新配置記憶體區塊的指標。  
  
> [!NOTE]
>  藉由擲回例外狀況不表示失敗的配置。 相反地，失敗的配置應該藉由傳回信號**NULL**。  
  
### <a name="remarks"></a>備註  
 呼叫[IAtlStringMgr::Free](#free)或[IAtlStringMgr::ReAllocate](#reallocate)釋放這個方法所配置的記憶體。  
  
> [!NOTE]
>  如需使用方式範例，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
##  <a name="clone"></a>  IAtlStringMgr::Clone  
 傳回新字串管理員搭配另一個執行個體的指標`CSimpleStringT`。  
  
```
IAtlStringMgr* Clone() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回一份`IAtlStringMgr`物件。  
  
### <a name="remarks"></a>備註  
 通常由架構呼叫字串管理員需要新的字串時。 在大部分情況下，**這**會傳回指標。  
  
 不過，如果 memory manager 不支援多個執行個體正在使用`CSimpleStringT`，應傳回共用字串管理員的指標。  
  
> [!NOTE]
>  如需使用方式範例，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
##  <a name="free"></a>  IAtlStringMgr::Free  
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
>  如需使用方式範例，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
##  <a name="getnilstring"></a>  IAtlStringMgr::GetNilString  
 傳回空字串的字串資料結構的指標。  
  
```
CStringData* GetNilString() throw();
```  
  
### <a name="return-value"></a>傳回值  
 指標`CStringData`物件用來表示空字串。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可傳回空的字串表示法。  
  
> [!NOTE]
>  在實作自訂字串管理員時，此函式必須永遠不會失敗。 您可以將內嵌的執行個體來確保這**CNilStringData**字串管理員類別，並傳回指標，該執行個體中。  
  
> [!NOTE]
>  如需使用方式範例，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
##  <a name="reallocate"></a>  IAtlStringMgr::Reallocate  
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
 在新的記憶體區塊中的字元數。  
  
 `nCharSize`  
 字串管理員所使用的字元類型的大小 （以位元組為單位）。  
  
### <a name="return-value"></a>傳回值  
 傳回新配置記憶體區塊開頭的指標。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可調整大小所指定之現有的記憶體區塊`pData`。  
  
 呼叫[IAtlStringMgr::Free](#free)釋放這個方法所配置的記憶體。  
  
> [!NOTE]
>  如需使用方式範例，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)


