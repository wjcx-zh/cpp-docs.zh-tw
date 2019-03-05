---
title: 服務對應巨集
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
ms.openlocfilehash: ab130b2401dc9885f82fd5668a2d722a96dd289b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290530"
---
# <a name="service-map-macros"></a>服務對應巨集

這些巨集會定義服務對應 」 和 「 項目。

|||
|-|-|
|[BEGIN_SERVICE_MAP](#begin_service_map)|標記 ATL 服務對應的開頭。|
|[END_SERVICE_MAP](#end_service_map)|將標記 ATL service map 的結尾。|
|[SERVICE_ENTRY](#service_entry)|指出物件支援特定的服務識別碼。|
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|會指示[IServiceProviderImpl::QueryService](#queryservice)鏈結到指定的物件。|

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="begin_service_map"></a>  BEGIN_SERVICE_MAP

標記服務對應的開頭。

```
BEGIN_SERVICE_MAP(theClass)
```

### <a name="parameters"></a>參數

*theClass*<br/>
[in]指定包含服務對應的類別。

### <a name="remarks"></a>備註

您可以使用服務對應來實作 COM 物件上的服務提供者的功能。 首先，您必須在此衍生您的類別，從[IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)。 有兩種類型的項目：

- [SERVICE_ENTRY](#service_entry)表示支援指定的服務識別碼 (SID)。

- [SERVICE_ENTRY_CHAIN](#service_entry_chain)指示[IServiceProviderImpl::QueryService](#queryservice)鏈結至另一個指定的物件。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]

##  <a name="end_service_map"></a>  END_SERVICE_MAP

結束標記的服務對應。

```
END_SERVICE_MAP()
```

### <a name="example"></a>範例

範例，請參閱[BEGIN_SERVICE_MAP](#begin_service_map)。

##  <a name="service_entry"></a>  SERVICE_ENTRY

指出物件是否支援所指定的服務識別碼*SID*。

```
SERVICE_ENTRY( SID )
```

### <a name="parameters"></a>參數

*SID*<br/>
服務識別碼。

### <a name="example"></a>範例

範例，請參閱[BEGIN_SERVICE_MAP](#begin_service_map)。

##  <a name="service_entry_chain"></a>  SERVICE_ENTRY_CHAIN

會指示[IServiceProviderImpl::QueryService](#queryservice)鏈結至所指定的物件*punk*。

```
SERVICE_ENTRY_CHAIN( punk )
```

### <a name="parameters"></a>參數

*punk*<br/>
指標**IUnknown**鏈結的介面。

### <a name="example"></a>範例

範例，請參閱[BEGIN_SERVICE_MAP](#begin_service_map)。

##  <a name="queryservice"></a>  IServiceProviderImpl::QueryService

建立或存取指定的服務，並傳回服務的指定介面的介面指標。

```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>參數

*guidService*<br/>
[in]為服務的識別項 (SID) 的指標。

*riid*<br/>
[in]呼叫端是來存取的介面識別項。

*ppvObj*<br/>
[out]受要求介面的間接指標。

### <a name="return-value"></a>傳回值

傳回的 HRESULT 值可以是下列其中一項：

|傳回值|意義|
|------------------|-------------|
|S_OK|服務已成功建立或擷取。|
|E_INVALIDARG|一或多個引數無效。|
|E_OUTOFMEMORY|記憶體不足，無法建立服務。|
|E_UNEXPECTED|發生未知的錯誤。|
|E_NOINTERFACE|要求的介面不是，此服務的一部分或未知的服務。|

### <a name="remarks"></a>備註

`QueryService` 傳回要求的介面，在指定的服務中的間接指標。 呼叫端負責釋放這個指標，當不再需要。

當您呼叫`QueryService`，則傳遞兩個服務識別項 (*guidService*) 和介面識別項 (*riid*)。 *GuidService*指定您要存取的服務並*riid*識別為服務一部分的介面。 另一方面，您會收到介面的間接指標。

實作介面的物件可能也會實作屬於其他服務的介面。 請考慮下列事項：

- 這些介面的一些可能是選擇性的。 並非所有的服務描述中定義的介面有一定在每個服務實作上或在每個傳回的物件。

- 不同於呼叫`QueryInterface`，傳遞不同的服務識別碼不一定代表會傳回不同的元件物件模型 (COM) 物件。

- 傳回的物件可能會有其他不屬於服務定義的介面。

兩個不同服務的詳細資訊，例如 SID_SMyService 和 SID_SYourService，可以同時使用相同的介面，即使指定介面的實作可能會有兩個服務之間的共通執行任何動作。 其運作，因為呼叫`QueryService`（SID_SMyService、 IID_IDispatch） 可以傳回不同物件，而非`QueryService`（SID_SYourService、 IID_IDispatch）。 當您指定不同的服務識別碼，是不會被視為物件識別。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
