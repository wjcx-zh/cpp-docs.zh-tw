---
title: IServiceProviderimpl 類別
ms.date: 11/04/2016
f1_keywords:
- IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl::QueryService
helpviewer_keywords:
- IServiceProviderImpl class
- IServiceProvider interface, ATL implementation
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
ms.openlocfilehash: ef0ee4f77441cb8d19ea2d6dcada1fed9faf2782
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329421"
---
# <a name="iserviceproviderimpl-class"></a>IServiceProviderimpl 類別

此類提供介面的`IServiceProvider`默認實現。

## <a name="syntax"></a>語法

```
template <class T>
class ATL_NO_VTABLE IServiceProviderImpl : public IServiceProvider
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`IServiceProviderImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IServiceProviderimpl:query服務](#queryservice)|創建或訪問指定的服務,並返回指向服務指定介面的介面指標。|

## <a name="remarks"></a>備註

介面`IServiceProvider`定位由其 GUID 指定的服務,並返回服務上請求的介面的介面指標。 類`IServiceProviderImpl`提供此介面的默認實現。

`IServiceProviderImpl`指定一種方法[:QueryService](#queryservice),它建立或訪問指定的服務,並返回指向服務指定介面的介面指標。

`IServiceProviderImpl`使用服務映射,從[BEGIN_SERVICE_MAP](service-map-macros.md#begin_service_map)開始,以[END_SERVICE_MAP](service-map-macros.md#end_service_map)結尾。

服務映射包含兩個條目[:SERVICE_ENTRY](service-map-macros.md#service_entry),它指示物件支援的指定服務 ID (SID),SERVICE_ENTRY_CHAIN 調用[SERVICE_ENTRY_CHAIN](service-map-macros.md#service_entry_chain)`QueryService`連結到另一個物件。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IServiceProvider`

`IServiceProviderImpl`

## <a name="requirements"></a>需求

**標題:** atlcom.h

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

[類別概觀](../../atl/atl-class-overview.md)
