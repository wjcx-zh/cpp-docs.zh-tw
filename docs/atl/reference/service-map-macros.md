---
title: 服務對應宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
ms.openlocfilehash: 1fa163098d89dd949c17ee7cd5e4ddc46cd2a091
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835203"
---
# <a name="service-map-macros"></a>服務對應宏

這些宏會定義服務對應和專案。

|名稱|描述|
|-|-|
|[BEGIN_SERVICE_MAP](#begin_service_map)|標記 ATL 服務對應的開頭。|
|[END_SERVICE_MAP](#end_service_map)|標記 ATL 服務對應的結尾。|
|[SERVICE_ENTRY](#service_entry)|表示物件支援特定的服務識別碼。|
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|指示 [IServiceProviderImpl：： QueryService](#queryservice) 與指定的物件連結。|

## <a name="requirements"></a>規格需求

**標頭：** atlcom.h。h

## <a name="begin_service_map"></a><a name="begin_service_map"></a> BEGIN_SERVICE_MAP

標記服務對應的開頭。

```
BEGIN_SERVICE_MAP(theClass)
```

### <a name="parameters"></a>參數

*theClass*<br/>
在指定包含服務對應的類別。

### <a name="remarks"></a>備註

使用服務對應，在您的 COM 物件上執行服務提供者功能。 首先，您必須從 [IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)衍生您的類別。 有兩種類型的專案：

- [SERVICE_ENTRY](#service_entry)   指出 (SID) 的指定服務識別碼支援。

- [SERVICE_ENTRY_CHAIN](#service_entry_chain)   指示 [IServiceProviderImpl：： QueryService](#queryservice) 與另一個指定的物件連結。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]

## <a name="end_service_map"></a><a name="end_service_map"></a> END_SERVICE_MAP

標記服務對應的結尾。

```
END_SERVICE_MAP()
```

### <a name="example"></a>範例

請參閱 [BEGIN_SERVICE_MAP](#begin_service_map)的範例。

## <a name="service_entry"></a><a name="service_entry"></a> SERVICE_ENTRY

表示物件支援 *SID*所指定的服務識別碼。

```
SERVICE_ENTRY( SID )
```

### <a name="parameters"></a>參數

*SID*<br/>
服務識別碼。

### <a name="example"></a>範例

請參閱 [BEGIN_SERVICE_MAP](#begin_service_map)的範例。

## <a name="service_entry_chain"></a><a name="service_entry_chain"></a> SERVICE_ENTRY_CHAIN

指示 [IServiceProviderImpl：： QueryService](#queryservice) 與 *punk*所指定的物件連結。

```
SERVICE_ENTRY_CHAIN( punk )
```

### <a name="parameters"></a>參數

*朋 克*<br/>
要連結的 **IUnknown** 介面指標。

### <a name="example"></a>範例

請參閱 [BEGIN_SERVICE_MAP](#begin_service_map)的範例。

## <a name="iserviceproviderimplqueryservice"></a><a name="queryservice"></a> IServiceProviderImpl：： QueryService

建立或存取指定的服務，並將介面指標傳回給服務的指定介面。

```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>參數

*guidService*<br/>
在服務識別碼 (SID) 的指標。

*riid*<br/>
在呼叫者要取得存取權的介面識別碼。

*ppvObj*<br/>
擴展要求的介面間接指標。

### <a name="return-value"></a>傳回值

傳回的 HRESULT 值是下列其中一項：

|傳回值|意義|
|------------------|-------------|
|S_OK|已成功建立或取出服務。|
|E_INVALIDARG|一或多個引數無效。|
|E_OUTOFMEMORY|記憶體不足，無法建立服務。|
|E_UNEXPECTED|發生未知的錯誤。|
|E_NOINTERFACE|要求的介面不是這項服務的一部分，或服務未知。|

### <a name="remarks"></a>備註

`QueryService` 傳回指定服務中所要求介面的間接指標。 當不再需要時，呼叫端會負責釋放這個指標。

當您呼叫時 `QueryService` ，會同時傳遞服務識別碼 (*GuidService*) 和介面識別碼 (*riid*) 。 *GuidService*會指定您想要存取的服務，而*riid*會識別屬於服務一部分的介面。 在傳回的情況下，您會收到介面的間接指標。

執行介面的物件也可以實作為其他服務一部分的介面。 請考慮下列事項：

- 其中一些介面可能是選擇性的。 並非在服務描述中定義的所有介面都必須存在於服務的每個執行或每個傳回的物件上。

- 不同于呼叫 `QueryInterface` ，傳遞不同的服務識別碼不一定表示會傳回不同的元件物件模型 (COM) 物件。

- 傳回的物件可能有其他不屬於服務定義一部分的介面。

這兩種不同的服務（例如 SID_SMyService 和 SID_SYourService）都可以指定使用相同的介面，即使介面的執行在這兩個服務之間可能沒有任何共通的專案也是一樣。 這是可行的，因為呼叫 `QueryService` (SID_SMyService、IID_IDispatch) 可能會傳回與 (SID_SYourService IID_IDispatch) 不同的物件 `QueryService` 。 當您指定不同的服務識別碼時，不會假設物件身分識別。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
