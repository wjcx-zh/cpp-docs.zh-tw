---
title: "IPersistStreamInitImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::IPersistStreamInitImpl
- ATL::IPersistStreamInitImpl<T>
- ATL.IPersistStreamInitImpl<T>
- IPersistStreamInitImpl
- ATL.IPersistStreamInitImpl
dev_langs:
- C++
helpviewer_keywords:
- IPersistStreamInit ATL implementation
- IPersistStreamInitImpl class
- streams, ATL
ms.assetid: ef217c3c-020f-4cf8-871e-ef68e57865b8
caps.latest.revision: 20
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: aa8427a891ac8d8e18ec7794a12e838a55bc23c8
ms.lasthandoff: 02/24/2017

---
# <a name="ipersiststreaminitimpl-class"></a>IPersistStreamInitImpl 類別
這個類別會實作**IUnknown** ，並提供的預設實作[IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273)介面。  
  
> [!IMPORTANT]
>  這個類別及其成員無法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式內使用。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>  
class ATL_NO_VTABLE IPersistStreamInitImpl 
   : public IPersistStreamInit
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IPersistStreamInitImpl`。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IPersistStreamInitImpl::GetClassID](#getclassid)|擷取物件的 CLSID。|  
|[IPersistStreamInitImpl::GetSizeMax](#getsizemax)|擷取儲存物件的資料所需的資料流的大小。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IPersistStreamInitImpl::InitNew](#initnew)|初始化新建立的物件。|  
|[IPersistStreamInitImpl::IsDirty](#isdirty)|檢查自上次儲存後，是否已變更物件的資料。|  
|[IPersistStreamInitImpl::Load](#load)|從指定的資料流載入物件的屬性。|  
|[IPersistStreamInitImpl::Save](#save)|將指定的資料流物件的屬性。|  
  
## <a name="remarks"></a>備註  
 [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273)介面可讓用戶端要求載入您的物件，並將持續性資料儲存至單一資料流。 類別`IPersistStreamInitImpl`提供此介面的預設實作，並且實作**IUnknown**傳送資訊給傾印裝置在偵錯組建。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IPersistStreamInit`  
  
 `IPersistStreamInitImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="a-namegetclassida--ipersiststreaminitimplgetclassid"></a><a name="getclassid"></a>IPersistStreamInitImpl::GetClassID  
 擷取物件的 CLSID。  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IPersist::GetClassID](http://msdn.microsoft.com/library/windows/desktop/ms688664)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetsizemaxa--ipersiststreaminitimplgetsizemax"></a><a name="getsizemax"></a>IPersistStreamInitImpl::GetSizeMax  
 擷取儲存物件的資料所需的資料流的大小。  
  
```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
### <a name="remarks"></a>備註  
 請參閱[IPersistStreamInit::GetSizeMax](http://msdn.microsoft.com/library/windows/desktop/ms687287)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameinitnewa--ipersiststreaminitimplinitnew"></a><a name="initnew"></a>IPersistStreamInitImpl::InitNew  
 初始化新建立的物件。  
  
```
STDMETHOD(InitNew)();
```  
  
### <a name="remarks"></a>備註  
 請參閱[IPersistStreamInit::InitNew](http://msdn.microsoft.com/library/windows/desktop/ms690234)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameisdirtya--ipersiststreaminitimplisdirty"></a><a name="isdirty"></a>IPersistStreamInitImpl::IsDirty  
 檢查自上次儲存後，是否已變更物件的資料。  
  
```
STDMETHOD(IsDirty)();
```  
  
### <a name="remarks"></a>備註  
 請參閱[IPersistStreamInit::IsDirty](http://msdn.microsoft.com/library/windows/desktop/ms680092)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameloada--ipersiststreaminitimplload"></a><a name="load"></a>IPersistStreamInitImpl::Load  
 從指定的資料流載入物件的屬性。  
  
```
STDMETHOD(Load)(LPSTREAM pStm);
```  
  
### <a name="remarks"></a>備註  
 ATL 使用物件的屬性對應，來擷取這項資訊。  
  
 請參閱[IPersistStreamInit::Load](http://msdn.microsoft.com/library/windows/desktop/ms680730)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesavea--ipersiststreaminitimplsave"></a><a name="save"></a>IPersistStreamInitImpl::Save  
 將指定的資料流物件的屬性。  
  
```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```  
  
### <a name="remarks"></a>備註  
 ATL 使用物件的屬性對應來儲存此資訊。  
  
 請參閱[IPersistStreamInit::Save](http://msdn.microsoft.com/library/windows/desktop/ms694439)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [儲存體和資料流](http://msdn.microsoft.com/library/windows/desktop/aa380352)   
 [類別概觀](../../atl/atl-class-overview.md)

