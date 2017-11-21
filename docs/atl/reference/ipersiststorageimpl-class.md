---
title: "IPersistStorageImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords:
- storage, ATL
- IPersistStorageImpl class
ms.assetid: d652f02c-239c-47c7-9a50-3e9fc3014fff
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3a8fb59d03bed295d28a88d9659205bd173a5355
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="ipersiststorageimpl-class"></a>IPersistStorageImpl 類別
這個類別會實作[IPersistStorage](http://msdn.microsoft.com/library/windows/desktop/ms679731)介面。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>  
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IPersistStorageImpl`。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[IPersistStorageImpl::GetClassID](#getclassid)|擷取物件的 CLSID。|  
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|指示要釋放所有的儲存體物件並輸入 HandsOff 模式的物件。 ATL 實作會傳回`S_OK`。|  
|[IPersistStorageImpl::InitNew](#initnew)|初始化新的存放裝置。|  
|[IPersistStorageImpl::IsDirty](#isdirty)|檢查自上次儲存後，是否已變更物件的資料。|  
|[IPersistStorageImpl::Load](#load)|從指定的儲存體中載入物件的屬性。|  
|[IPersistStorageImpl::Save](#save)|將物件的屬性儲存至指定的儲存體。|  
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|告知可返回一般模式將寫入其儲存體物件的物件。 ATL 實作會傳回`S_OK`。|  
  
## <a name="remarks"></a>備註  
 `IPersistStorageImpl`實作[IPersistStorage](http://msdn.microsoft.com/library/windows/desktop/ms679731)介面，可讓用戶端要求的物件載入並儲存使用的儲存體持續性資料。  
  
 這個類別的實作必須有類別`T`進行的實作`IPersistStreamInit`可透過介面`QueryInterface`。 通常這表示該類別`T`應衍生自[IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)，提供的項目`IPersistStreamInit`中[COM 對應](http://msdn.microsoft.com/library/ead2a1e3-334d-44ad-bb1f-b94bb14c2333)，並使用[屬性對應](http://msdn.microsoft.com/library/bfe30be6-62c3-4dc2-bd49-21ef96f15427)來描述此類別的永續性資料。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IPersistStorage`  
  
 `IPersistStorageImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="getclassid"></a>IPersistStorageImpl::GetClassID  
 擷取物件的 CLSID。  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>備註  
 請參閱[ipersist:: Getclassid](http://msdn.microsoft.com/library/windows/desktop/ms688664) Windows SDK 中。  
  
##  <a name="handsoffstorage"></a>IPersistStorageImpl::HandsOffStorage  
 指示要釋放所有的儲存體物件並輸入 HandsOff 模式的物件。  
  
```
STDMETHOD(HandsOffStorage)(void);
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 請參閱[IPersistStorage::HandsOffStorage](http://msdn.microsoft.com/library/windows/desktop/ms679742) Windows SDK 中。  
  
##  <a name="initnew"></a>IPersistStorageImpl::InitNew  
 初始化新的存放裝置。  
  
```
STDMETHOD(InitNew)(IStorage*);
```  
  
### <a name="remarks"></a>備註  
 ATL 實作會委派至[IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273)介面。  
  
 請參閱[IPersistStorage:InitNew](http://msdn.microsoft.com/library/windows/desktop/ms687194) Windows SDK 中。  
  
##  <a name="isdirty"></a>IPersistStorageImpl::IsDirty  
 檢查自上次儲存後，是否已變更物件的資料。  
  
```
STDMETHOD(IsDirty)(void);
```  
  
### <a name="remarks"></a>備註  
 ATL 實作會委派至[IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273)介面。  
  
 請參閱[IPersistStorage:IsDirty](http://msdn.microsoft.com/library/windows/desktop/ms683910) Windows SDK 中。  
  
##  <a name="load"></a>IPersistStorageImpl::Load  
 從指定的儲存體中載入物件的屬性。  
  
```
STDMETHOD(Load)(IStorage* pStorage);
```  
  
### <a name="remarks"></a>備註  
 ATL 實作會委派至[IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273)介面。 **負載**使用名為 「 內容 」 的資料流中擷取物件的資料。 [儲存](#save)方法原本會建立此資料流。  
  
 請參閱[IPersistStorage:Load](http://msdn.microsoft.com/library/windows/desktop/ms680557) Windows SDK 中。  
  
##  <a name="save"></a>IPersistStorageImpl::Save  
 將物件的屬性儲存至指定的儲存體。  
  
```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```  
  
### <a name="remarks"></a>備註  
 ATL 實作會委派至[IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273)介面。 當**儲存**這是第一次呼叫，它會建立指定的儲存體上名為 「 內容 」 的資料流。 這個資料流之後會用來稍後呼叫**儲存**在呼叫[負載](#load)。  
  
 請參閱[IPersistStorage:Save](http://msdn.microsoft.com/library/windows/desktop/ms680680) Windows SDK 中。  
  
##  <a name="savecompleted"></a>IPersistStorageImpl::SaveCompleted  
 告知可返回一般模式將寫入其儲存體物件的物件。  
  
```
STDMETHOD(SaveCompleted)(IStorage*);
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 請參閱[IPersistStorage:SaveCompleted](http://msdn.microsoft.com/library/windows/desktop/ms679713) Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [儲存體和資料流](http://msdn.microsoft.com/library/windows/desktop/aa380352)   
 [IPersistStreamInitImpl 類別](../../atl/reference/ipersiststreaminitimpl-class.md)   
 [IPersistPropertyBagImpl 類別](../../atl/reference/ipersistpropertybagimpl-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
