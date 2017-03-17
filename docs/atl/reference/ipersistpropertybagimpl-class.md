---
title: "IPersistPropertyBagImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl::GetClassID
- ATLCOM/ATL::IPersistPropertyBagImpl::InitNew
- ATLCOM/ATL::IPersistPropertyBagImpl::Load
- ATLCOM/ATL::IPersistPropertyBagImpl::Save
dev_langs:
- C++
helpviewer_keywords:
- IPersistPropertyBagImpl class
ms.assetid: 712af24d-99f8-40f2-9811-53b3ff6e5b19
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
ms.openlocfilehash: 901a6a6bf4097b6aa78a898254766f122bb2f959
ms.lasthandoff: 02/24/2017

---
# <a name="ipersistpropertybagimpl-class"></a>IPersistPropertyBagImpl 類別
這個類別會實作**IUnknown** ，可讓物件將其內容儲存到用戶端提供的屬性包。  
  
> [!IMPORTANT]
>  這個類別及其成員無法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式內使用。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>  
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IPersistPropertyBagImpl`。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[IPersistPropertyBagImpl::GetClassID](#getclassid)|擷取物件的 CLSID。|  
|[IPersistPropertyBagImpl::InitNew](#initnew)|初始化新建立的物件。 ATL 實作會傳回`S_OK`。|  
|[IPersistPropertyBagImpl::Load](#load)|從用戶端提供的屬性包中載入物件的屬性。|  
|[IPersistPropertyBagImpl::Save](#save)|將物件的屬性儲存至用戶端提供的屬性包。|  
  
## <a name="remarks"></a>備註  
 [IPersistPropertyBag](https://msdn.microsoft.com/library/aa768205.aspx)介面可讓用戶端提供的屬性包來儲存其屬性的物件。 類別`IPersistPropertyBagImpl`提供此介面的預設實作，並且實作**IUnknown**傳送資訊給傾印裝置在偵錯組建。  
  
 **IPersistPropertyBag**可搭配[IPropertyBag](https://msdn.microsoft.com/library/aa768196.aspx)和[IErrorLog](https://msdn.microsoft.com/library/aa768231.aspx)。 這些後面的兩個介面必須由用戶端實作。 透過`IPropertyBag`，用戶端儲存及載入物件的個別屬性。 透過**IErrorLog**、 物件和用戶端可以報告遇到的任何錯誤。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IPersistPropertyBag`  
  
 `IPersistPropertyBagImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="getclassid"></a>IPersistPropertyBagImpl::GetClassID  
 擷取物件的 CLSID。  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IPersist::GetClassID](http://msdn.microsoft.com/library/windows/desktop/ms688664)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="initnew"></a>IPersistPropertyBagImpl::InitNew  
 初始化新建立的物件。  
  
```
STDMETHOD(InitNew)();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 請參閱[IPersistPropertyBag::InitNew](https://msdn.microsoft.com/library/aa768204.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="load"></a>IPersistPropertyBagImpl::Load  
 從用戶端提供的屬性包中載入物件的屬性。  
  
```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```  
  
### <a name="remarks"></a>備註  
 ATL 使用物件的屬性對應，來擷取這項資訊。  
  
 請參閱[IPersistPropertyBag::Load](https://msdn.microsoft.com/library/aa768206.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="save"></a>IPersistPropertyBagImpl::Save  
 將物件的屬性儲存至用戶端提供的屬性包。  
  
```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```  
  
### <a name="remarks"></a>備註  
 ATL 使用物件的屬性對應來儲存此資訊。 根據預設，這個方法會儲存所有的屬性，不論值*fSaveAllProperties*。  
  
 請參閱[IPersistPropertyBag::Save](https://msdn.microsoft.com/library/aa768207.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [BEGIN_PROP_MAP](http://msdn.microsoft.com/library/bfe30be6-62c3-4dc2-bd49-21ef96f15427)   
 [類別概觀](../../atl/atl-class-overview.md)

