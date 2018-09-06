---
title: IServiceProviderImpl 類別 |Microsoft Docs
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
ms.openlocfilehash: ca7a39149969b7e85685930d6e901bf81db99d64
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43759393"
---
# <a name="iserviceproviderimpl-class"></a>IServiceProviderImpl 類別

這個類別提供的預設實作`IServiceProvider`介面。

## <a name="syntax"></a>語法

```
template <class T>  
class ATL_NO_VTABLE IServiceProviderImpl : public IServiceProvider
```

#### <a name="parameters"></a>參數

*T*  
您的類別，衍生自`IServiceProviderImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IServiceProviderImpl::QueryService](#queryservice)|建立或存取指定的服務，並傳回服務的指定介面的介面指標。|

## <a name="remarks"></a>備註

`IServiceProvider`介面會找出其 GUID 指定的服務，並傳回服務所要求介面的介面指標。 類別`IServiceProviderImpl`提供此介面的預設實作。

`IServiceProviderImpl` 指定一種方法： [QueryService](#queryservice)，這會建立或存取指定的服務，並傳回服務的指定介面的介面指標。

`IServiceProviderImpl` 會使用服務對應，開頭[BEGIN_SERVICE_MAP](service-map-macros.md#begin_service_map)起[END_SERVICE_MAP](service-map-macros.md#end_service_map)。

服務對應包含兩個項目： [SERVICE_ENTRY](service-map-macros.md#service_entry)，表示支援的物件，指定的服務識別碼 (SID) 和[SERVICE_ENTRY_CHAIN](service-map-macros.md#service_entry_chain)，其會呼叫`QueryService`鏈結至另一個物件。

## <a name="inheritance-hierarchy"></a>繼承階層

`IServiceProvider`

`IServiceProviderImpl`

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="queryservice"></a>  IServiceProviderImpl::QueryService

建立或存取指定的服務，並傳回服務的指定介面的介面指標。

```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>參數

[IN]*guidService*  
為服務的識別項 (SID) 的指標。

[IN]*riid*  
呼叫端是來存取的介面識別項。

[OUT]*ppvObj*  
受要求介面的間接指標。

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

[類別概觀](../../atl/atl-class-overview.md)
