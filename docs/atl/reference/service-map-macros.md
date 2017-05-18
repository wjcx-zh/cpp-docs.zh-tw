---
title: "服務對應巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: eea45a3315237c77eff0231d485111cefb8557cc
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="service-map-macros"></a>服務對應巨集
這些巨集定義服務對應和項目。  
  
|||  
|-|-|  
|[BEGIN_SERVICE_MAP](#begin_service_map)|標記 ATL 服務對應的開頭。|  
|[END_SERVICE_MAP](#end_service_map)|ATL 服務對應結束標記。|  
|[SERVICE_ENTRY](#service_entry)|指出物件支援特定的服務識別碼。|  
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|指示[IServiceProviderImpl::QueryService](#queryservice)鏈結至指定的物件。|  

## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
   
##  <a name="begin_service_map"></a>BEGIN_SERVICE_MAP  
 標示服務對應的開頭。  
  
```
BEGIN_SERVICE_MAP(theClass)
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 [in]指定包含服務對應的類別。  
  
### <a name="remarks"></a>備註  
 使用服務對應來實作 COM 物件上的服務提供者功能。 首先，您必須衍生您的類別，從[IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)。 有兩種類型的項目︰  
  
- [SERVICE_ENTRY](#service_entry)表示支援指定的服務識別碼 (SID)。  
  
- [SERVICE_ENTRY_CHAIN](#service_entry_chain)指示[IServiceProviderImpl::QueryService](#queryservice)鏈結至另一個指定的物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM&#57;](../../atl/codesnippet/cpp/service-map-macros_1.h)]  
  
##  <a name="end_service_map"></a>END_SERVICE_MAP  
 標示服務對應的結束。  
  
```
END_SERVICE_MAP()
```  
  
### <a name="example"></a>範例  
 請參閱範例[BEGIN_SERVICE_MAP](#begin_service_map)。  
  
##  <a name="service_entry"></a>SERVICE_ENTRY  
 指出物件是否支援所指定的服務識別碼*SID*。  
  
```
SERVICE_ENTRY( SID )
```  
  
### <a name="parameters"></a>參數  
 *SID*  
 服務識別碼。  
  
### <a name="example"></a>範例  
 請參閱範例[BEGIN_SERVICE_MAP](#begin_service_map)。  
  
##  <a name="service_entry_chain"></a>SERVICE_ENTRY_CHAIN  
 指示[IServiceProviderImpl::QueryService](#queryservice)鏈結所指定的物件至`punk`。  
  
```
SERVICE_ENTRY_CHAIN( punk )
```  
  
### <a name="parameters"></a>參數  
 `punk`  
 指標**IUnknown**鏈結的介面。  
  
### <a name="example"></a>範例  
 請參閱範例[BEGIN_SERVICE_MAP](#begin_service_map)。  
  
##  <a name="queryservice"></a>IServiceProviderImpl::QueryService  
 建立或存取指定的服務，並傳回服務的指定介面的介面指標。  
  
```
STDMETHOD(QueryService)( 
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>參數  
 [IN]`guidService`  
 服務識別碼 (SID) 的指標。  
  
 [IN]`riid`  
 呼叫者是能夠存取的介面識別項。  
  
 [OUT]`ppvObj`  
 所要求介面的間接指標。  
  
### <a name="return-value"></a>傳回值  
 傳回`HRESULT`值可以是下列其中之一︰  
  
|傳回值|意義|  
|------------------|-------------|  
|S_OK|服務已順利建立或擷取。|  
|E_INVALIDARG|一或多個引數無效。|  
|E_OUTOFMEMORY|記憶體不足，無法建立服務。|  
|E_UNEXPECTED|發生未知的錯誤。|  
|E_NOINTERFACE|要求的介面不是這項服務的一部分或未知的服務。|  
  
### <a name="remarks"></a>備註  
 `QueryService`傳回所要求的介面中指定的服務的間接指標。 呼叫端會負責在發行時不再需要這個指標。  
  
 當您呼叫`QueryService`，則傳遞兩個服務識別項 ( `guidService`) 和介面識別碼 ( `riid`)。 `guidService`指定您想要存取的服務和`riid`識別服務的介面。 您會收到間接的介面指標。  
  
 實作介面的物件可能也會實作屬於其他服務的介面。 請考慮下列事項：  
  
-   這些介面的一些可能是選擇性的。 並非所有服務描述中定義的介面都有一定是服務的每個實作或每個傳回的物件。  
  
-   不同於呼叫`QueryInterface`，傳遞不同的服務識別碼不一定會傳回不同的元件物件模型 (COM) 物件。  
  
-   傳回的物件可能有其他不屬於服務的定義的介面。  
  
 兩個不同的服務，例如 SID_SMyService 和 SID_SYourService，可以同時指定要使用相同的介面，即使介面的實作可能會有兩個服務之間執行任何動作。 這樣可以運作，因為呼叫`QueryService`（SID_SMyService、 IID_IDispatch） 可能會傳回不同的物件比`QueryService`（SID_SYourService、 IID_IDispatch）。 物件識別不會被視為，當您指定不同的服務識別項。  
  
## <a name="see-also"></a>另請參閱  
 [巨集](../../atl/reference/atl-macros.md)

