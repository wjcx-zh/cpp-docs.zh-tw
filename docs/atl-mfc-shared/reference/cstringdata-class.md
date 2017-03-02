---
title: "CStringData 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStringData
dev_langs:
- C++
helpviewer_keywords:
- CStringData class
- shared classes, CStringData
ms.assetid: 4e31b5ca-3dbe-4fd5-b692-8211fbfb2593
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: b7dfebebbec7acc774fa2e63ab9fafed788f679a
ms.lasthandoff: 02/24/2017

---
# <a name="cstringdata-class"></a>CStringData 類別
這個類別表示字串物件的資料。  
  
## <a name="syntax"></a>語法  
  
```
struct CStringData
```  
  
## <a name="members"></a>Members  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddRef](#addref)|字串資料物件的參考計數遞增。|  
|[data](#data)|擷取字串物件中的字元資料。|  
|[IsLocked](#islocked)|決定是否相關聯的字串物件的緩衝區已被鎖定。|  
|[IsShared](#isshared)|決定是否目前共用相關聯的字串物件的緩衝區。|  
|[鎖定](#lock)|鎖定相關聯的字串物件的緩衝區。|  
|[發行](#release)|釋放指定的字串物件。|  
|[解除鎖定](#unlock)|解除鎖定相關聯的字串物件的緩衝區。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|[nAllocLength](#nalloclength)|配置中的資料長度`XCHAR`s （不含結束 null)|  
|[nDataLength](#ndatalength)|目前使用中的資料長度`XCHAR`s （不含結束 null)|  
|[nRefs](#nrefs)|物件的目前參考計數。|  
|[pStringMgr](#pstringmgr)|字串管理員，這個字串物件的指標。|  
  
## <a name="remarks"></a>備註  
 這個類別只供開發人員實作自訂字串管理員。 如需有關自訂字串管理員的詳細資訊，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)  
  
 這個類別會封裝各種類型的資訊與資料相關聯的使用更高版本的字串物件，例如[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)， [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)，或[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)物件。 較高的每個字串物件包含與其相關聯的指標`CStringData`物件，讓多個指向相同的字串資料物件的字串物件。 此關聯性由參考計數 ( `nRefs`) 的`CStringData`物件。  
  
> [!NOTE]
>  在某些情況下，字串型別 (例如**CFixedString**) 不會共用與多個更高版本的字串物件的字串資料物件。 如需詳細資訊，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
 這項資料所組成︰  
  
-   記憶體管理員 (型別[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)) 的字串。  
  
-   目前的長度 ( [nDataLength](#ndatalength)) 的字串。  
  
-   已配置的長度 ( [nAllocLength](#nalloclength)) 的字串。 基於效能考量，這可能不同於目前字串的長度  
  
-   目前的參考計數 ( [nRefs](#nrefs)) 的`CStringData`物件。 這個值會用來決定字串物件的數目會共用相同`CStringData`物件。  
  
-   實際的字元緩衝區 ([資料](#data)) 的字串。  
  
    > [!NOTE]
    >  實際的字元緩衝區的字串物件配置字串管理員，並附加至`CStringData`物件。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlsimpstr.h  
  
##  <a name="a-nameaddrefa--cstringdataaddref"></a><a name="addref"></a>CStringData::AddRef  
 字串物件的參考計數遞增。  
  
```
void AddRef() throw();
```  
  
### <a name="remarks"></a>備註  
 字串物件的參考計數遞增。  
  
> [!NOTE]
>  因為負計數會指出字串緩衝區已鎖定，沒有負面的參考計數，在字串上呼叫這個方法。  
  
##  <a name="a-namedataa--cstringdatadata"></a><a name="data"></a>CStringData::data  
 傳回字串物件的字元緩衝區的指標。  
  
```
void* data() throw();
```  
  
### <a name="return-value"></a>傳回值  
 字元緩衝區的字串物件的指標。  
  
### <a name="remarks"></a>備註  
 呼叫此函式來傳回關聯的字串物件的目前字元緩衝區。  
  
> [!NOTE]
>  這個緩衝區未配置的`CStringData`物件但字串管理員時所需。 配置時，緩衝區會附加至字串資料物件。  
  
##  <a name="a-nameislockeda--cstringdataislocked"></a><a name="islocked"></a>CStringData::IsLocked  
 決定是否字元緩衝區已被鎖定。  
  
```
bool IsLocked() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回**true**如果緩衝區已鎖定，否則**false**。  
  
### <a name="remarks"></a>備註  
 呼叫此函式來判斷是否字串物件的字元緩衝區目前已鎖定。  
  
##  <a name="a-nameisshareda--cstringdataisshared"></a><a name="isshared"></a>CStringData::IsShared  
 決定是否要共用的字元緩衝區。  
  
```
bool IsShared() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回**true**如果緩衝區已共用，否則**false**。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可判斷字元緩衝區的字串資料物件目前在多個字串物件中共用。  
  
##  <a name="a-namelocka--cstringdatalock"></a><a name="lock"></a>CStringData::Lock  
 鎖定相關聯的字串物件的字元緩衝區。  
  
```
void Lock() throw();
```  
  
### <a name="remarks"></a>備註  
 呼叫此函式的字串資料物件的字元緩衝區中鎖定。 鎖定與解除鎖定，是由開發人員都需要字元緩衝區的直接存取時使用。 示範使用鎖定的例子是[LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer)和[UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer)方法`CSimpleStringT`。  
  
> [!NOTE]
>  如果緩衝區不共用更高版本的字串物件，可以只鎖定字元緩衝區。  
  
##  <a name="a-namenalloclengtha--cstringdatanalloclength"></a><a name="nalloclength"></a>CStringData::nAllocLength  
 已配置的字元緩衝區的長度。  
  
```
int nAllocLength;
```  
  
### <a name="remarks"></a>備註  
 儲存的配置的資料緩衝區的長度`XCHAR`s （不含結束 null)。  
  
##  <a name="a-namendatalengtha--cstringdatandatalength"></a><a name="ndatalength"></a>CStringData::nDataLength  
 目前字串物件的長度。  
  
```
int nDataLength;
```  
  
### <a name="remarks"></a>備註  
 儲存目前使用中的資料長度`XCHAR`s （不含結束 null)。  
  
##  <a name="a-namenrefsa--cstringdatanrefs"></a><a name="nrefs"></a>CStringData::nRefs  
 字串資料物件的參考計數。  
  
```
long nRefs;
```  
  
### <a name="remarks"></a>備註  
 儲存字串資料物件的參考計數。 這個計數代表較高層的字串資料的物件相關聯的字串物件的數目。 負值則表示目前鎖定的字串資料物件。  
  
##  <a name="a-namepstringmgra--cstringdatapstringmgr"></a><a name="pstringmgr"></a>CStringData::pStringMgr  
 關聯的字串物件的記憶體管理員。  
  
```
IAtlStringMgr* pStringMgr;
```  
  
### <a name="remarks"></a>備註  
 儲存相關聯的字串物件的記憶體管理員。 如需記憶體管理員和字串的詳細資訊，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
##  <a name="a-namereleasea--cstringdatarelease"></a><a name="release"></a>CStringData::Release  
 字串資料物件的參考計數遞減。  
  
```
void Release() throw();
```  
  
### <a name="remarks"></a>備註  
 呼叫此函式，以遞減參考計數，釋放`CStringData`結構如果參考計數達到零。 這通常是當字串物件被刪除，並因此不再需要參考的字串資料物件。  
  
 例如，下列程式碼可以呼叫`CStringData::Release`字串資料物件與相關聯`str1`:  
  
 [!code-cpp[NVC_ATLMFC_Utilities #&104;](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]  
  
##  <a name="a-nameunlocka--cstringdataunlock"></a><a name="unlock"></a>CStringData::Unlock  
 解除鎖定相關聯的字串物件的字元緩衝區。  
  
```
void Unlock() throw();
```  
  
### <a name="remarks"></a>備註  
 呼叫此函式可解除鎖定的字串資料物件的字元緩衝區。 當緩衝區已解除鎖定時，便可共用，而可參考計數。  
  
> [!NOTE]
>  每次呼叫`Lock`必須有相符的對應呼叫`Unlock`。  
  
 當開發人員必須確定不共用的字串資料時，會使用鎖定與解除鎖定。 示範使用鎖定的例子是[LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer)和[UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer)方法`CSimpleStringT`。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)



