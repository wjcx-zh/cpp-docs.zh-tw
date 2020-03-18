---
title: 服務對應宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
ms.openlocfilehash: ab130b2401dc9885f82fd5668a2d722a96dd289b
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417471"
---
# <a name="service-map-macros"></a>服務對應宏

這些宏會定義服務對應和專案。

|||
|-|-|
|[BEGIN_SERVICE_MAP](#begin_service_map)|標記 ATL 服務對應的開頭。|
|[END_SERVICE_MAP](#end_service_map)|標示 ATL 服務對應的結尾。|
|[SERVICE_ENTRY](#service_entry)|表示物件支援特定的服務識別碼。|
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|指示[IServiceProviderImpl：： QueryService](#queryservice)連結至指定的物件。|

## <a name="requirements"></a>需求

**標頭：** atlcom.h。h

##  <a name="begin_service_map"></a>BEGIN_SERVICE_MAP

標記服務對應的開頭。

```
BEGIN_SERVICE_MAP(theClass)
```

### <a name="parameters"></a>參數

*theClass*<br/>
在指定包含服務對應的類別。

### <a name="remarks"></a>備註

使用服務對應，在您的 COM 物件上執行服務提供者功能。 首先，您必須從[IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)衍生您的類別。 有兩種類型的專案：

- [SERVICE_ENTRY](#service_entry)  表示對指定服務識別碼（SID）的支援。

- [SERVICE_ENTRY_CHAIN](#service_entry_chain)  指示[IServiceProviderImpl：： QueryService](#queryservice)連結至另一個指定的物件。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]

##  <a name="end_service_map"></a>END_SERVICE_MAP

標示服務對應的結尾。

```
END_SERVICE_MAP()
```

### <a name="example"></a>範例

請參閱[BEGIN_SERVICE_MAP](#begin_service_map)的範例。

##  <a name="service_entry"></a>SERVICE_ENTRY

表示物件支援*SID*所指定的服務識別碼。

```
SERVICE_ENTRY( SID )
```

### <a name="parameters"></a>參數

*SID*<br/>
服務識別碼。

### <a name="example"></a>範例

請參閱[BEGIN_SERVICE_MAP](#begin_service_map)的範例。

##  <a name="service_entry_chain"></a>SERVICE_ENTRY_CHAIN

指示[IServiceProviderImpl：： QueryService](#queryservice)連結至*punk*所指定的物件。

```
SERVICE_ENTRY_CHAIN( punk )
```

### <a name="parameters"></a>參數

*punk*<br/>
要連結之**IUnknown**介面的指標。

### <a name="example"></a>範例

請參閱[BEGIN_SERVICE_MAP](#begin_service_map)的範例。

##  <a name="queryservice"></a>IServiceProviderImpl：： QueryService

建立或存取指定的服務，並將介面指標傳回給服務的指定介面。

```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>參數

*guidService*<br/>
在服務識別碼（SID）的指標。

*riid*<br/>
在呼叫端要取得存取權的介面識別碼。

*ppvObj*<br/>
脫銷所要求介面的間接指標。

### <a name="return-value"></a>傳回值

傳回的 HRESULT 值是下列其中一項：

|傳回值|意義|
|------------------|-------------|
|S_OK|已成功建立或抓取服務。|
|E_INVALIDARG|一或多個引數無效。|
|E_OUTOFMEMORY|記憶體不足，無法建立服務。|
|E_UNEXPECTED|發生不明錯誤。|
|E_NOINTERFACE|要求的介面不是此服務的一部分，或服務不明。|

### <a name="remarks"></a>備註

`QueryService` 會在指定的服務中傳回所要求介面的間接指標。 呼叫端會在不再需要時，負責釋放此指標。

當您呼叫 `QueryService`時，您會同時傳遞服務識別碼（*guidService*）和介面識別碼（*riid*）。 *GuidService*會指定您要存取的服務，而*riid*會識別屬於服務一部分的介面。 在 return 中，您會收到介面的間接指標。

執行介面的物件可能也會實作為其他服務之一部分的介面。 請考慮下列：

- 其中一些介面可能是選擇性的。 並非服務描述中定義的所有介面都一定會出現在服務的每個執行或每個傳回的物件上。

- 不同于 `QueryInterface`的呼叫，傳遞不同的服務識別碼不一定表示傳回不同的元件物件模型（COM）物件。

- 傳回的物件可能會有不屬於服務定義一部分的其他介面。

兩個不同的服務（例如 SID_SMyService 和 SID_SYourService）都可以指定使用相同的介面，即使介面的執行可能在兩個服務之間沒有任何共同的功能。 這是可行的，因為 `QueryService` （SID_SMyService，IID_IDispatch）的呼叫可能會傳回與 `QueryService` （SID_SYourService，IID_IDispatch）不同的物件。 當您指定不同的服務識別碼時，不會假設物件身分識別。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
