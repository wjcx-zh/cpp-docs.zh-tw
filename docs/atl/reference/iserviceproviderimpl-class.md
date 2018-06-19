---
title: IServiceProviderImpl 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl::QueryService
dev_langs:
- C++
helpviewer_keywords:
- IServiceProviderImpl class
- IServiceProvider interface, ATL implementation
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b1472fe5d952e93b45240128383db9fdec5b093
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363670"
---
# <a name="iserviceproviderimpl-class"></a>IServiceProviderImpl 類別
這個類別提供的預設實作`IServiceProvider`介面。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>  
class ATL_NO_VTABLE IServiceProviderImpl : public IServiceProvider
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IServiceProviderImpl`。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IServiceProviderImpl::QueryService](#queryservice)|建立或存取指定的服務，並將介面指標傳回指定服務的介面。|  
  
## <a name="remarks"></a>備註  
 `IServiceProvider`介面找出其 GUID 所指定的服務，並在服務上傳回所要求介面的介面指標。 類別`IServiceProviderImpl`提供此介面的預設實作。  
  
 **IServiceProviderImpl**指定其中一種方法： [QueryService](#queryservice)，建立或存取指定的服務，並將介面指標傳回指定服務的介面。  
  
 `IServiceProviderImpl` 使用服務對應，開頭[BEGIN_SERVICE_MAP](service-map-macros.md#begin_service_map)結束[END_SERVICE_MAP](service-map-macros.md#end_service_map)。  
  
 服務對應包含兩個項目： [SERVICE_ENTRY](service-map-macros.md#service_entry)，表示支援的物件，指定的服務識別碼 (SID) 和[SERVICE_ENTRY_CHAIN](service-map-macros.md#service_entry_chain)，而它會呼叫`QueryService`鏈結至另一個物件。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IServiceProvider`  
  
 `IServiceProviderImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="queryservice"></a>  IServiceProviderImpl::QueryService  
 建立或存取指定的服務，並將介面指標傳回指定服務的介面。  
  
```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>參數  
 [IN] `guidService`  
 服務識別碼 (SID) 的指標。  
  
 [IN] `riid`  
 呼叫者是能夠存取的介面識別項。  
  
 [OUT] `ppvObj`  
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
 `QueryService` 傳回所要求的介面中指定的服務的間接指標。 呼叫端會負責在發行時不再需要這個指標。  
  
 當您呼叫`QueryService`，您傳遞兩個服務識別元 ( `guidService`) 和介面識別項 ( `riid`)。 `guidService`指定您要存取的服務和`riid`識別為服務一部分的介面。 您會收到介面間接指標。  
  
 實作介面的物件可能也可實作屬於其他服務的介面。 請考慮下列事項：  
  
-   這些介面的某些可能會是選擇性的。 並非所有的服務描述中定義的介面有一定在每個服務實作或每個傳回的物件上。  
  
-   不同於呼叫`QueryInterface`，傳遞不同的服務識別碼不一定表示會傳回不同的元件物件模型 (COM) 物件。  
  
-   傳回的物件可能不是服務定義的一部分的其他介面。  
  
 兩個不同的服務，例如 SID_SMyService 和 SID_SYourService，可以同時指定要使用相同的介面，即使介面的實作可能會有兩個服務之間執行任何動作。 其運作，因為呼叫`QueryService`（SID_SMyService、 IID_IDispatch） 可能會傳回不同的物件，而非`QueryService`（SID_SYourService、 IID_IDispatch）。 當您指定不同的服務識別項，不會假設物件識別。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
