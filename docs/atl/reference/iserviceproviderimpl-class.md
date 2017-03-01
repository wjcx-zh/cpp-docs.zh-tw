---
title: "IServiceProviderImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::IServiceProviderImpl<T>
- ATL.IServiceProviderImpl<T>
- ATL.IServiceProviderImpl
- ATL::IServiceProviderImpl
- IServiceProviderImpl
dev_langs:
- C++
helpviewer_keywords:
- IServiceProviderImpl class
- IServiceProvider interface, ATL implementation
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
caps.latest.revision: 22
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
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 69a59fe23b3ca787dee86b1bbdc6775a44903f91
ms.lasthandoff: 02/24/2017

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
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[IServiceProviderImpl::QueryService](#queryservice)|建立或存取指定的服務，並傳回服務的指定介面的介面指標。|  
  
## <a name="remarks"></a>備註  
 `IServiceProvider`介面尋找服務，由其 GUID，並傳回服務的要求之介面的介面指標。 類別`IServiceProviderImpl`提供此介面的預設實作。  
  
 **IServiceProviderImpl**指定其中一個方法︰ [QueryService](#queryservice)，這會建立或存取指定的服務並返回服務的指定介面的介面指標。  
  
 `IServiceProviderImpl`使用服務對應，以開始[BEGIN_SERVICE_MAP](http://msdn.microsoft.com/library/3c6ae156-8776-4588-8227-2d234daec236) ，並以結束[END_SERVICE_MAP](http://msdn.microsoft.com/library/9a35d02a-014c-413a-bb0b-bcca11ab45a6)。  
  
 服務對應包含兩個項目︰ [SERVICE_ENTRY](http://msdn.microsoft.com/library/e65ff9cc-15e8-41cf-b686-f99eb6686ca9)，表示支援的物件，指定的服務識別碼 (SID) 和[SERVICE_ENTRY_CHAIN](http://msdn.microsoft.com/library/09be4ce4-3ccd-4ff2-a95e-a9d5275354c1)，而它會呼叫`QueryService`鏈結至另一個物件。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IServiceProvider`  
  
 `IServiceProviderImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="a-namequeryservicea--iserviceproviderimplqueryservice"></a><a name="queryservice"></a>IServiceProviderImpl::QueryService  
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
 [類別概觀](../../atl/atl-class-overview.md)

