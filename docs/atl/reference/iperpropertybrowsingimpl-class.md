---
title: "IPerPropertyBrowsingImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetDisplayString
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedStrings
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedValue
- ATLCTL/ATL::IPerPropertyBrowsingImpl::MapPropertyToPage
dev_langs:
- C++
helpviewer_keywords:
- IPerPropertyBrowsingImpl class
- property pages, accessing information
- IPerPropertyBrowsing, ATL implementation
ms.assetid: 0b1a9be3-d242-4767-be69-663a21e4b728
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dca0c4e519703408af1ca5b6834e4b311c70bd21
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="iperpropertybrowsingimpl-class"></a>IPerPropertyBrowsingImpl 類別
這個類別會實作**IUnknown**並可讓用戶端存取物件的屬性頁中的資訊。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```

template <class T>
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :
    public IPerPropertyBrowsing
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IPerPropertyBrowsingImpl`。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IPerPropertyBrowsingImpl::GetDisplayString](#getdisplaystring)|擷取字串，描述指定的屬性。|  
|[IPerPropertyBrowsingImpl::GetPredefinedStrings](#getpredefinedstrings)|擷取指定的屬性可以接受的值相對應字串的陣列。|  
|[IPerPropertyBrowsingImpl::GetPredefinedValue](#getpredefinedvalue)|擷取**VARIANT**包含所指定的 DISPID 識別屬性的值。 從擷取的字串名稱是相關聯 DISPID `GetPredefinedStrings`。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IPerPropertyBrowsingImpl::MapPropertyToPage](#mappropertytopage)|擷取與指定屬性相關聯的屬性頁的 CLSID。|  
  
## <a name="remarks"></a>備註  
 [IPerPropertyBrowsing](http://msdn.microsoft.com/library/windows/desktop/ms678432)介面允許用戶端存取物件的屬性頁中的資訊。 類別`IPerPropertyBrowsingImpl`提供此介面的預設實作，並實作**IUnknown**資訊傳送給傾印裝置在偵錯組建。  
  
> [!NOTE]
>  如果您使用 Microsoft Access 作為容器應用程式，您必須在衍生類別從`IPerPropertyBrowsingImpl`。 否則，存取不會載入您的控制項。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IPerPropertyBrowsing`  
  
 `IPerPropertyBrowsingImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlctl.h  
  
##  <a name="getdisplaystring"></a>IPerPropertyBrowsingImpl::GetDisplayString  
 擷取字串，描述指定的屬性。  
  
```
STDMETHOD(GetDisplayString)(
    DISPID dispID,
    BSTR* pBstr);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IPerPropertyBrowsing::GetDisplayString](http://msdn.microsoft.com/library/windows/desktop/ms688734) Windows SDK 中。  
  
##  <a name="getpredefinedstrings"></a>IPerPropertyBrowsingImpl::GetPredefinedStrings  
 填滿零個項目每個陣列。  
  
```
STDMETHOD(GetPredefinedStrings)(
    DISPID dispID,
    CALPOLESTR* pCaStringsOut,
    CADWORD* pCaCookiesOut);
```  
  
### <a name="return-value"></a>傳回值  
 ATL 的實作[GetPredefinedValue](#getpredefinedvalue)傳回**E_NOTIMPL**。  
  
### <a name="remarks"></a>備註  
 請參閱[IPerPropertyBrowsing::GetPredefinedStrings](http://msdn.microsoft.com/library/windows/desktop/ms679724) Windows SDK 中。  
  
##  <a name="getpredefinedvalue"></a>IPerPropertyBrowsingImpl::GetPredefinedValue  
 擷取**VARIANT**包含所指定的 DISPID 識別屬性的值。 從擷取的字串名稱是相關聯 DISPID `GetPredefinedStrings`。  
  
```
STDMETHOD(GetPredefinedValue)(
    DISPID dispID,
    DWORD dwCookie,
    VARIANT* pVarOut);
```  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
### <a name="remarks"></a>備註  
 ATL 的實作[GetPredefinedStrings](#getpredefinedstrings)擷取任何對應的字串。  
  
 請參閱[IPerPropertyBrowsing::GetPredefinedValue](http://msdn.microsoft.com/library/windows/desktop/ms690401) Windows SDK 中。  
  
##  <a name="mappropertytopage"></a>IPerPropertyBrowsingImpl::MapPropertyToPage  
 擷取與指定屬性相關聯的屬性頁的 CLSID。  
  
```
STDMETHOD(MapPropertyToPage)(
    DISPID dispID,
    CLSID* pClsid);
```  
  
### <a name="remarks"></a>備註  
 ATL 會使用物件的屬性對應，來取得這項資訊。  
  
 請參閱[IPerPropertyBrowsing::MapPropertyToPage](http://msdn.microsoft.com/library/windows/desktop/ms694476) Windows SDK 中。  
  
## <a name="see-also"></a>請參閱  
 [IPropertyPageImpl 類別](../../atl/reference/ipropertypageimpl-class.md)   
 [ISpecifyPropertyPagesImpl 類別](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
