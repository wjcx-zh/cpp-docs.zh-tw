---
title: "IPersistPropertyBagImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: abef2ffa759cf74ee2316c7e0c9dd84f5c76b1d7
ms.contentlocale: zh-tw
ms.lasthandoff: 03/31/2017

---
# <a name="ipersistpropertybagimpl-class"></a>IPersistPropertyBagImpl 類別
這個類別會實作**IUnknown** ，並可讓用戶端提供的屬性包以儲存其屬性的物件。  
  
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
  
|名稱|描述|  
|----------|-----------------|  
|[IPersistPropertyBagImpl::GetClassID](#getclassid)|擷取物件的 CLSID。|  
|[IPersistPropertyBagImpl::InitNew](#initnew)|初始化新建立的物件。 ATL 實作會傳回`S_OK`。|  
|[IPersistPropertyBagImpl::Load](#load)|從用戶端提供的屬性包中載入物件的屬性。|  
|[IPersistPropertyBagImpl::Save](#save)|將物件的屬性儲存到用戶端提供的屬性包。|  
  
## <a name="remarks"></a>備註  
 [IPersistPropertyBag](https://msdn.microsoft.com/library/aa768205.aspx)介面可讓用戶端提供的屬性包以儲存其屬性的物件。 類別`IPersistPropertyBagImpl`提供此介面的預設實作，並實作**IUnknown**資訊傳送給傾印裝置在偵錯組建。  
  
 **IPersistPropertyBag**可搭配[IPropertyBag](https://msdn.microsoft.com/library/aa768196.aspx)和[IErrorLog](https://msdn.microsoft.com/library/aa768231.aspx)。 用戶端必須實作這些後者的兩個介面。 透過`IPropertyBag`，用戶端會將儲存並載入物件的個別屬性。 透過**IErrorLog**，物件與用戶端可以報告遇到的任何錯誤。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IPersistPropertyBag`  
  
 `IPersistPropertyBagImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcom.h  
  
##  <a name="getclassid"></a>IPersistPropertyBagImpl::GetClassID  
 擷取物件的 CLSID。  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>備註  
 請參閱[ipersist:: Getclassid](http://msdn.microsoft.com/library/windows/desktop/ms688664)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
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
 ATL 會使用物件的屬性對應，來擷取這項資訊。  
  
 請參閱[IPersistPropertyBag::Load](https://msdn.microsoft.com/library/aa768206.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="save"></a>IPersistPropertyBagImpl::Save  
 將物件的屬性儲存到用戶端提供的屬性包。  
  
```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```  
  
### <a name="remarks"></a>備註  
 ATL 會使用物件的屬性對應儲存這項資訊。 根據預設，這個方法會儲存所有屬性的值為何*fSaveAllProperties*。  
  
 請參閱[IPersistPropertyBag::Save](https://msdn.microsoft.com/library/aa768207.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)   
 [類別概觀](../../atl/atl-class-overview.md)

