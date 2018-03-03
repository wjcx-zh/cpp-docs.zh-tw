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
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
dev_langs:
- C++
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 444d89833d84f23099ff0de8bce29bfc9d0a1344
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="service-map-macros"></a>服務對應巨集
這些巨集會定義服務對應和項目。  
  
|||  
|-|-|  
|[BEGIN_SERVICE_MAP](#begin_service_map)|標記的 ATL 服務對應的開頭。|  
|[END_SERVICE_MAP](#end_service_map)|ATL 服務對應結束標記。|  
|[SERVICE_ENTRY](#service_entry)|指出物件支援特定的服務識別碼。|  
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|指示[IServiceProviderImpl::QueryService](#queryservice)鏈結至指定的物件。|  

## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
   
##  <a name="begin_service_map"></a>BEGIN_SERVICE_MAP  
 標記服務對應的開頭。  
  
```
BEGIN_SERVICE_MAP(theClass)
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 [in]指定包含服務對應的類別。  
  
### <a name="remarks"></a>備註  
 使用服務對應來實作服務提供者功能在您的 COM 物件上。 首先，您必須衍生您的類別從[IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)。 有兩種類型的項目：  
  
- [SERVICE_ENTRY](#service_entry)表示支援指定的服務識別碼 (SID)。  
  
- [SERVICE_ENTRY_CHAIN](#service_entry_chain)指示[IServiceProviderImpl::QueryService](#queryservice)鏈結至另一個指定的物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]  
  
##  <a name="end_service_map"></a>END_SERVICE_MAP  
 標示服務對應的結尾。  
  
```
END_SERVICE_MAP()
```  
  
### <a name="example"></a>範例  
 請參閱範例的[BEGIN_SERVICE_MAP](#begin_service_map)。  
  
##  <a name="service_entry"></a>SERVICE_ENTRY  
 指出物件是否支援所指定的服務識別碼*SID*。  
  
```
SERVICE_ENTRY( SID )
```  
  
### <a name="parameters"></a>參數  
 *SID*  
 服務識別碼。  
  
### <a name="example"></a>範例  
 請參閱範例的[BEGIN_SERVICE_MAP](#begin_service_map)。  
  
##  <a name="service_entry_chain"></a>SERVICE_ENTRY_CHAIN  
 指示[IServiceProviderImpl::QueryService](#queryservice)鏈結所指定的物件至`punk`。  
  
```
SERVICE_ENTRY_CHAIN( punk )
```  
  
### <a name="parameters"></a>參數  
 `punk`  
 指標**IUnknown**鏈結的介面。  
  
### <a name="example"></a>範例  
 請參閱範例的[BEGIN_SERVICE_MAP](#begin_service_map)。  
  
##  <a name="queryservice"></a>IServiceProviderImpl::QueryService  
 建立或存取指定的服務，並將介面指標傳回指定服務的介面。  
  
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
 傳回`HRESULT`值可以是下列其中之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|S_OK|已成功建立或擷取服務的時間。|  
|E_INVALIDARG|一或多個引數無效。|  
|E_OUTOFMEMORY|記憶體不足，無法建立服務。|  
|E_UNEXPECTED|發生未知的錯誤。|  
|E_NOINTERFACE|要求的介面不是這項服務的一部分或未知的服務。|  
  
### <a name="remarks"></a>備註  
 `QueryService`傳回所要求的介面中指定的服務的間接指標。 呼叫端會負責在發行時不再需要這個指標。  
  
 當您呼叫`QueryService`，您傳遞兩個服務識別元 ( `guidService`) 和介面識別項 ( `riid`)。 `guidService`指定您要存取的服務和`riid`識別為服務一部分的介面。 您會收到介面間接指標。  
  
 實作介面的物件可能也可實作屬於其他服務的介面。 請考慮下列事項：  
  
-   這些介面的某些可能會是選擇性的。 並非所有的服務描述中定義的介面有一定在每個服務實作或每個傳回的物件上。  
  
-   不同於呼叫`QueryInterface`，傳遞不同的服務識別碼不一定表示會傳回不同的元件物件模型 (COM) 物件。  
  
-   傳回的物件可能不是服務定義的一部分的其他介面。  
  
 兩個不同的服務，例如 SID_SMyService 和 SID_SYourService，可以同時指定要使用相同的介面，即使介面的實作可能會有兩個服務之間執行任何動作。 其運作，因為呼叫`QueryService`（SID_SMyService、 IID_IDispatch） 可能會傳回不同的物件，而非`QueryService`（SID_SYourService、 IID_IDispatch）。 當您指定不同的服務識別項，不會假設物件識別。  
  
## <a name="see-also"></a>請參閱  
 [巨集](../../atl/reference/atl-macros.md)
