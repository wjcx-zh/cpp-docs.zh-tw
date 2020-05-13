---
title: 服務對應宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
ms.openlocfilehash: eb2fe41c79135a7ac2ced9bc3242b070170716b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325933"
---
# <a name="service-map-macros"></a>服務對應宏

這些宏定義服務映射和條目。

|||
|-|-|
|[BEGIN_SERVICE_MAP](#begin_service_map)|標記 ATL 服務映射的開頭。|
|[END_SERVICE_MAP](#end_service_map)|標記 ATL 服務映射的末尾。|
|[SERVICE_ENTRY](#service_entry)|指示物件支援特定的服務 ID。|
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|指示[IServiceProviderImpl:query 服務](#queryservice)連結到指定的物件。|

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="begin_service_map"></a><a name="begin_service_map"></a>BEGIN_SERVICE_MAP

標記服務映射的開頭。

```
BEGIN_SERVICE_MAP(theClass)
```

### <a name="parameters"></a>參數

*類別*<br/>
[在]指定包含服務對應的類。

### <a name="remarks"></a>備註

使用服務映射在 COM 物件上實現服務提供者功能。 首先,您必須從[IServiceProviderImpl 派生](../../atl/reference/iserviceproviderimpl-class.md)您的類。 有兩種類型的項目:

- [SERVICE_ENTRY](#service_entry)  指示對指定服務 ID (SID) 的支援。

- [SERVICE_ENTRY_CHAIN](#service_entry_chain)  指示[IServiceProviderImpl:query 服務](#queryservice)連結到另一個指定的物件。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]

## <a name="end_service_map"></a><a name="end_service_map"></a>END_SERVICE_MAP

標記服務映射的末尾。

```
END_SERVICE_MAP()
```

### <a name="example"></a>範例

請參閱[BEGIN_SERVICE_MAP](#begin_service_map)的示例。

## <a name="service_entry"></a><a name="service_entry"></a>SERVICE_ENTRY

指示物件支援*SID*指定的服務 ID。

```
SERVICE_ENTRY( SID )
```

### <a name="parameters"></a>參數

*希*<br/>
服務 ID。

### <a name="example"></a>範例

請參閱[BEGIN_SERVICE_MAP](#begin_service_map)的示例。

## <a name="service_entry_chain"></a><a name="service_entry_chain"></a>SERVICE_ENTRY_CHAIN

指示[IServiceProviderImpl:query 服務](#queryservice)連結到*朋克*指定的物件。

```
SERVICE_ENTRY_CHAIN( punk )
```

### <a name="parameters"></a>參數

*龐克*<br/>
指向要連結的**I 未知**介面的指標。

### <a name="example"></a>範例

請參閱[BEGIN_SERVICE_MAP](#begin_service_map)的示例。

## <a name="iserviceproviderimplqueryservice"></a><a name="queryservice"></a>IServiceProviderimpl:query服務

創建或訪問指定的服務,並返回指向服務指定介面的介面指標。

```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>參數

*吉德服務*<br/>
[在]指向服務標識碼 (SID) 的指標。

*riid*<br/>
[在]呼叫方要造訪的介面的標識符。

*普夫奧比*<br/>
[出]間接指標指向請求的介面。

### <a name="return-value"></a>傳回值

傳回的 HRESULT 值為以下值之一:

|傳回值|意義|
|------------------|-------------|
|S_OK|已成功創建或檢索服務。|
|E_INVALIDARG|一或多個引數無效。|
|E_OUTOFMEMORY|記憶體不足以創建服務。|
|E_UNEXPECTED|發生未知的錯誤。|
|E_NOINTERFACE|請求的介面不是此服務的一部分,或者服務未知。|

### <a name="remarks"></a>備註

`QueryService`返回指向指定服務中請求的介面的間接指標。 調用方負責在不再需要此指標時釋放它。

呼叫`QueryService`時 ,將傳遞服務識別碼 *(guidService*) 和介面識別碼 *(riid)。* *guidService*指定要存取的服務 *,riid*識別屬於服務的介面。 作為回報,您將收到指向介面的間接指標。

實現介面的物件還可能實現屬於其他服務的介面。 請考慮下列：

- 其中一些介面可能是可選的。 服務描述中定義的介面並非都一定存在於服務的每個實現或每個返回的物件上。

- 與調用`QueryInterface`不同,傳遞不同的服務標識符並不一定意味著返回不同的元件物件模型 (COM) 物件。

- 返回的物件可能具有不屬於服務定義的其他介面。

兩個不同的服務(如SID_SMyService和SID_SYourService)都可以指定同一介面的使用,即使該介面的實現在兩個服務之間可能沒有任何共同之處。 這工作正常,因為對`QueryService`(SID_SMyService、IID_IDispatch) 的調用可以`QueryService`返回與 (SID_SYourService、IID_IDispatch) 不同的物件。 指定其他服務標識碼時,不會假定對象標識。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
