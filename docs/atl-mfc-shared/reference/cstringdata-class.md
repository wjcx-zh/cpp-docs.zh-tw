---
title: "CStringData 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStringData
- ATLSIMPSTR/ATL::CStringData
- ATLSIMPSTR/ATL::AddRef
- ATLSIMPSTR/ATL::data
- ATLSIMPSTR/ATL::IsLocked
- ATLSIMPSTR/ATL::IsShared
- ATLSIMPSTR/ATL::Lock
- ATLSIMPSTR/ATL::Release
- ATLSIMPSTR/ATL::Unlock
- ATLSIMPSTR/ATL::nAllocLength
- ATLSIMPSTR/ATL::nDataLength
- ATLSIMPSTR/ATL::nRefs
- ATLSIMPSTR/ATL::pStringMgr
dev_langs:
- C++
helpviewer_keywords:
- CStringData class
- shared classes, CStringData
ms.assetid: 4e31b5ca-3dbe-4fd5-b692-8211fbfb2593
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7523ca52c0ded8ec9b3cf02dd6798beca8be5cf8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cstringdata-class"></a>CStringData 類別
此類別代表 string 物件的資料。  
  
## <a name="syntax"></a>語法  
  
```
struct CStringData
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddRef](#addref)|字串資料物件的參考計數遞增。|  
|[data](#data)|擷取字元資料的字串物件。|  
|[IsLocked](#islocked)|決定是否相關聯的 string 物件的緩衝區已被鎖定。|  
|[IsShared](#isshared)|決定相關聯的 string 物件的緩衝區目前在共用。|  
|[鎖定](#lock)|鎖定相關聯的 string 物件的緩衝區。|  
|[發行](#release)|釋放指定的字串物件。|  
|[解除鎖定](#unlock)|解除鎖定相關聯的 string 物件的緩衝區。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|[nAllocLength](#nalloclength)|配置中的資料長度`XCHAR`s （不包括結束 null)|  
|[nDataLength](#ndatalength)|目前使用中的資料長度`XCHAR`s （不包括結束 null)|  
|[nRefs](#nrefs)|物件的目前參考計數。|  
|[pStringMgr](#pstringmgr)|字串管理員，這個字串物件的指標。|  
  
## <a name="remarks"></a>備註  
 這個類別僅供開發人員實作自訂字串管理員。 如需有關自訂字串管理員的詳細資訊，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)  
  
 這個類別會封裝各種類型的資訊與資料相關聯的更高版本的字串物件，例如[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)， [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)，或[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)物件。 較高的每個字串物件包含與其相關聯的指標`CStringData`物件，讓多個字串物件，以指向相同的字串資料物件。 此關聯性由參考計數 ( `nRefs`) 的`CStringData`物件。  
  
> [!NOTE]
>  在某些情況下，字串型別 (例如**CFixedString**) 不會共用與多個更高版本的字串物件的字串資料的物件。 如需詳細資訊，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
 這項資料組成：  
  
-   記憶體管理員 (型別[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)) 的字串。  
  
-   目前的長度 ( [nDataLength](#ndatalength)) 的字串。  
  
-   已配置的長度 ( [nAllocLength](#nalloclength)) 的字串。 基於效能考量，這可以不同於目前字串的長度  
  
-   目前的參考計數 ( [nRefs](#nrefs)) 的`CStringData`物件。 這個值會用來決定多少的字串物件共用相同`CStringData`物件。  
  
-   實際的字元緩衝區 ([資料](#data)) 的字串。  
  
    > [!NOTE]
    >  實際的字元緩衝區的字串物件配置字串管理員，並附加至`CStringData`物件。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlsimpstr.h  
  
##  <a name="addref"></a>CStringData::AddRef  
 字串物件的參考計數遞增。  
  
```
void AddRef() throw();
```  
  
### <a name="remarks"></a>備註  
 字串物件的參考計數遞增。  
  
> [!NOTE]
>  因為為負數計數表示字串緩衝區已鎖定，沒有字串上的負的參考計數，呼叫這個方法。  
  
##  <a name="data"></a>CStringData::data  
 傳回字串物件中的字元緩衝區的指標。  
  
```
void* data() throw();
```  
  
### <a name="return-value"></a>傳回值  
 String 物件的字元緩衝區的指標。  
  
### <a name="remarks"></a>備註  
 呼叫此函式來傳回關聯的字串物件的目前字元緩衝區。  
  
> [!NOTE]
>  這個緩衝區不會配置所`CStringData`物件但字串管理員時所需。 配置時，緩衝區會附加至字串資料物件。  
  
##  <a name="islocked"></a>CStringData::IsLocked  
 決定是否已鎖定的字元緩衝區。  
  
```
bool IsLocked() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回**true**如果緩衝區已鎖定，否則**false**。  
  
### <a name="remarks"></a>備註  
 呼叫此函式來判斷是否字串物件中的字元緩衝區目前已鎖定。  
  
##  <a name="isshared"></a>CStringData::IsShared  
 決定是否要共用的字元緩衝區。  
  
```
bool IsShared() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回**true**如果緩衝區已共用，否則**false**。  
  
### <a name="remarks"></a>備註  
 呼叫此函式來判斷是否字串資料物件中的字元緩衝區目前在多個字串物件之間共用。  
  
##  <a name="lock"></a>CStringData::Lock  
 鎖定相關聯的 string 物件的字元緩衝區。  
  
```
void Lock() throw();
```  
  
### <a name="remarks"></a>備註  
 呼叫此函式可鎖定字元緩衝區的字串資料物件。 鎖定和解除鎖定，是由開發人員都需要直接存取的字元緩衝區時使用。 鎖定的理想範例示範[LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer)和[UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer)方法`CSimpleStringT`。  
  
> [!NOTE]
>  如果在更高版本的字串物件之間共用的緩衝區不只可以鎖定字元緩衝區。  
  
##  <a name="nalloclength"></a>CStringData::nAllocLength  
 已配置的字元緩衝區的長度。  
  
```
int nAllocLength;
```  
  
### <a name="remarks"></a>備註  
 儲存的配置的資料緩衝區的長度`XCHAR`s （不包括結束 null)。  
  
##  <a name="ndatalength"></a>CStringData::nDataLength  
 目前 string 物件的長度。  
  
```
int nDataLength;
```  
  
### <a name="remarks"></a>備註  
 儲存目前使用中的資料長度`XCHAR`s （不包括結束 null)。  
  
##  <a name="nrefs"></a>CStringData::nRefs  
 String 資料物件的參考計數。  
  
```
long nRefs;
```  
  
### <a name="remarks"></a>備註  
 儲存字串資料物件的參考計數。 這個計數代表更高版本的字串資料的物件相關聯的 string 物件的數目。 負值則表示目前鎖定了字串資料物件。  
  
##  <a name="pstringmgr"></a>CStringData::pStringMgr  
 相關聯的 string 物件的記憶體管理員。  
  
```
IAtlStringMgr* pStringMgr;
```  
  
### <a name="remarks"></a>備註  
 會儲存相關聯的字串物件的記憶體管理員。 如需有關記憶體管理員和字串的詳細資訊，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
##  <a name="release"></a>CStringData::Release  
 遞減參考計數的字串資料的物件。  
  
```
void Release() throw();
```  
  
### <a name="remarks"></a>備註  
 呼叫此函式，以遞減參考計數，釋放`CStringData`結構如果參考計數達到零。 這通常是字串物件遭到刪除，而且因此不再需要時參考字串資料物件。  
  
 例如，下列程式碼可以呼叫`CStringData::Release`字串資料物件與相關聯的`str1`:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#104](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]  
  
##  <a name="unlock"></a>CStringData::Unlock  
 解除鎖定相關聯的 string 物件的字元緩衝區。  
  
```
void Unlock() throw();
```  
  
### <a name="remarks"></a>備註  
 呼叫此函式可解除鎖定字元緩衝區的字串資料物件。 緩衝區未鎖定之後，它是可共用，而且可以參考計數。  
  
> [!NOTE]
>  每次呼叫`Lock`必須有相符的對應呼叫`Unlock`。  
  
 鎖定和解除鎖定，是開發人員必須確保不共用的字串資料時使用。 鎖定的理想範例示範[LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer)和[UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer)方法`CSimpleStringT`。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)


