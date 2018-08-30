---
title: IPerPropertyBrowsingImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c018b5c7ffa8e72ae9ce68fb23799d712a879df8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206672"
---
# <a name="iperpropertybrowsingimpl-class"></a>IPerPropertyBrowsingImpl 類別
這個類別會實作`IUnknown`，並可讓用戶端來存取物件的屬性頁中的資訊。  
  
> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```

template <class T>
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :
    public IPerPropertyBrowsing
```  
  
#### <a name="parameters"></a>參數  
 *T*  
 您的類別，衍生自`IPerPropertyBrowsingImpl`。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IPerPropertyBrowsingImpl::GetDisplayString](#getdisplaystring)|擷取字串，描述指定的屬性。|  
|[IPerPropertyBrowsingImpl::GetPredefinedStrings](#getpredefinedstrings)|擷取對應至指定的屬性可以接受的值的字串陣列。|  
|[IPerPropertyBrowsingImpl::GetPredefinedValue](#getpredefinedvalue)|擷取變數，包含所指定的 DISPID 識別屬性的值。 從擷取的字串名稱是相關聯的 DISPID `GetPredefinedStrings`。 ATL 實作會傳回 E_NOTIMPL。|  
|[IPerPropertyBrowsingImpl::MapPropertyToPage](#mappropertytopage)|擷取指定的屬性相關聯的屬性頁 CLSID。|  
  
## <a name="remarks"></a>備註  
 [IPerPropertyBrowsing](/windows/desktop/api/ocidl/nn-ocidl-iperpropertybrowsing)介面允許用戶端存取物件的屬性頁中的資訊。 類別`IPerPropertyBrowsingImpl`提供此介面的預設實作，並實作`IUnknown`資訊傳送給傾印裝置在偵錯組建。  
  
> [!NOTE]
>  如果您使用 Microsoft Access 作為容器應用程式，您必須衍生您的類別，從`IPerPropertyBrowsingImpl`。 否則，存取將不會載入您的控制項。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IPerPropertyBrowsing`  
  
 `IPerPropertyBrowsingImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlctl.h  
  
##  <a name="getdisplaystring"></a>  IPerPropertyBrowsingImpl::GetDisplayString  
 擷取字串，描述指定的屬性。  
  
```
STDMETHOD(GetDisplayString)(
    DISPID dispID,
    BSTR* pBstr);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IPerPropertyBrowsing::GetDisplayString](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-getdisplaystring) Windows SDK 中。  
  
##  <a name="getpredefinedstrings"></a>  IPerPropertyBrowsingImpl::GetPredefinedStrings  
 填滿零個項目每個陣列。  
  
```
STDMETHOD(GetPredefinedStrings)(
    DISPID dispID,
    CALPOLESTR* pCaStringsOut,
    CADWORD* pCaCookiesOut);
```  
  
### <a name="return-value"></a>傳回值  
 ATL 的實作[GetPredefinedValue](#getpredefinedvalue)傳回 E_NOTIMPL。  
  
### <a name="remarks"></a>備註  
 請參閱[IPerPropertyBrowsing::GetPredefinedStrings](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedstrings) Windows SDK 中。  
  
##  <a name="getpredefinedvalue"></a>  IPerPropertyBrowsingImpl::GetPredefinedValue  
 擷取變數，包含所指定的 DISPID 識別屬性的值。 從擷取的字串名稱是相關聯的 DISPID `GetPredefinedStrings`。  
  
```
STDMETHOD(GetPredefinedValue)(
    DISPID dispID,
    DWORD dwCookie,
    VARIANT* pVarOut);
```  
  
### <a name="return-value"></a>傳回值  
 傳回 E_NOTIMPL。  
  
### <a name="remarks"></a>備註  
 ATL 的實作[GetPredefinedStrings](#getpredefinedstrings)會抓取沒有對應的字串。  
  
 請參閱[IPerPropertyBrowsing::GetPredefinedValue](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedvalue) Windows SDK 中。  
  
##  <a name="mappropertytopage"></a>  IPerPropertyBrowsingImpl::MapPropertyToPage  
 擷取與指定的屬性相關聯的屬性頁 CLSID。  
  
```
STDMETHOD(MapPropertyToPage)(
    DISPID dispID,
    CLSID* pClsid);
```  
  
### <a name="remarks"></a>備註  
 ATL 會使用物件的屬性對應，以取得此資訊。  
  
 請參閱[IPerPropertyBrowsing::MapPropertyToPage](/windows/desktop/api/ocidl/nf-ocidl-iperpropertybrowsing-mappropertytopage) Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [IPropertyPageImpl 類別](../../atl/reference/ipropertypageimpl-class.md)   
 [ISpecifyPropertyPagesImpl 類別](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
