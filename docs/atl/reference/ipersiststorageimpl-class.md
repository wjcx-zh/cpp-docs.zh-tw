---
title: IPersistStorageImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl::GetClassID
- ATLCOM/ATL::IPersistStorageImpl::HandsOffStorage
- ATLCOM/ATL::IPersistStorageImpl::InitNew
- ATLCOM/ATL::IPersistStorageImpl::IsDirty
- ATLCOM/ATL::IPersistStorageImpl::Load
- ATLCOM/ATL::IPersistStorageImpl::Save
- ATLCOM/ATL::IPersistStorageImpl::SaveCompleted
dev_langs:
- C++
helpviewer_keywords:
- storage, ATL
- IPersistStorageImpl class
ms.assetid: d652f02c-239c-47c7-9a50-3e9fc3014fff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08cde95cf7ce680137aa932eb9642b9cd910318a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43223209"
---
# <a name="ipersiststorageimpl-class"></a>IPersistStorageImpl 類別
這個類別會實作[IPersistStorage](/windows/desktop/api/objidl/nn-objidl-ipersiststorage)介面。  
  
> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>  
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```  
  
#### <a name="parameters"></a>參數  
 *T*  
 您的類別，衍生自`IPersistStorageImpl`。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IPersistStorageImpl::GetClassID](#getclassid)|擷取物件的 CLSID。|  
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|指示要釋放所有的儲存體物件並輸入 HandsOff 模式的物件。 ATL 實作會傳回 S_OK。|  
|[IPersistStorageImpl::InitNew](#initnew)|初始化新的儲存體。|  
|[IPersistStorageImpl::IsDirty](#isdirty)|會檢查自上次儲存後，是否已變更物件的資料。|  
|[IPersistStorageImpl::Load](#load)|從指定的儲存體中載入物件的屬性。|  
|[IPersistStorageImpl::Save](#save)|將指定的儲存體物件的屬性。|  
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|通知可以回到正常模式才能寫入至其儲存體物件的物件。 ATL 實作會傳回 S_OK。|  
  
## <a name="remarks"></a>備註  
 `IPersistStorageImpl` 會實作[IPersistStorage](/windows/desktop/api/objidl/nn-objidl-ipersiststorage)介面，可讓用戶端要求的物件載入並儲存持續性資料使用儲存體。  
  
 這個類別的實作需要類別`T`進行的實作`IPersistStreamInit`可透過介面`QueryInterface`。 通常這表示該類別`T`應該衍生自[IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)，提供的項目`IPersistStreamInit`中[COM 對應](https://msdn.microsoft.com/library/ead2a1e3-334d-44ad-bb1f-b94bb14c2333)，並使用[屬性對應](https://msdn.microsoft.com/library/bfe30be6-62c3-4dc2-bd49-21ef96f15427)來描述類別的永續性資料。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IPersistStorage`  
  
 `IPersistStorageImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="getclassid"></a>  IPersistStorageImpl::GetClassID  
 擷取物件的 CLSID。  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IPersist::GetClassID](/windows/desktop/api/objidl/nf-objidl-ipersist-getclassid) Windows SDK 中。  
  
##  <a name="handsoffstorage"></a>  IPersistStorageImpl::HandsOffStorage  
 指示要釋放所有的儲存體物件並輸入 HandsOff 模式的物件。  
  
```
STDMETHOD(HandsOffStorage)(void);
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK。  
  
### <a name="remarks"></a>備註  
 請參閱[IPersistStorage::HandsOffStorage](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-handsoffstorage) Windows SDK 中。  
  
##  <a name="initnew"></a>  IPersistStorageImpl::InitNew  
 初始化新的儲存體。  
  
```
STDMETHOD(InitNew)(IStorage*);
```  
  
### <a name="remarks"></a>備註  
 ATL 實作會委派給[IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit)介面。  
  
 請參閱[IPersistStorage:InitNew](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-initnew) Windows SDK 中。  
  
##  <a name="isdirty"></a>  IPersistStorageImpl::IsDirty  
 會檢查自上次儲存後，是否已變更物件的資料。  
  
```
STDMETHOD(IsDirty)(void);
```  
  
### <a name="remarks"></a>備註  
 ATL 實作會委派給[IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit)介面。  
  
 請參閱[IPersistStorage:IsDirty](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-isdirty) Windows SDK 中。  
  
##  <a name="load"></a>  IPersistStorageImpl::Load  
 從指定的儲存體中載入物件的屬性。  
  
```
STDMETHOD(Load)(IStorage* pStorage);
```  
  
### <a name="remarks"></a>備註  
 ATL 實作會委派給[IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit)介面。 `Load` 您可以使用名為 [內容] 的資料流來擷取物件的資料。 [儲存](#save)方法原本建立此資料流。  
  
 請參閱[IPersistStorage:Load](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-load) Windows SDK 中。  
  
##  <a name="save"></a>  IPersistStorageImpl::Save  
 將指定的儲存體物件的屬性。  
  
```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```  
  
### <a name="remarks"></a>備註  
 ATL 實作會委派給[IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit)介面。 當`Save`這是第一次呼叫，它會建立名為指定的儲存體上的 [內容] 的資料流。 這個資料流則會在稍後呼叫`Save`及呼叫[負載](#load)。  
  
 請參閱[IPersistStorage:Save](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-save) Windows SDK 中。  
  
##  <a name="savecompleted"></a>  IPersistStorageImpl::SaveCompleted  
 通知可以回到正常模式才能寫入至其儲存體物件的物件。  
  
```
STDMETHOD(SaveCompleted)(IStorage*);
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK。  
  
### <a name="remarks"></a>備註  
 請參閱[IPersistStorage:SaveCompleted](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-savecompleted) Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [儲存體和資料流](/windows/desktop/Stg/storages-and-streams)   
 [IPersistStreamInitImpl 類別](../../atl/reference/ipersiststreaminitimpl-class.md)   
 [IPersistPropertyBagImpl 類別](../../atl/reference/ipersistpropertybagimpl-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
