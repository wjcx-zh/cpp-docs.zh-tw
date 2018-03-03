---
title: "IDispEventSimpleImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl::Advise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventAdvise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventUnadvise
- ATLCOM/ATL::IDispEventSimpleImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventSimpleImpl::Invoke
- ATLCOM/ATL::IDispEventSimpleImpl::Unadvise
dev_langs:
- C++
helpviewer_keywords:
- IDispEventSimpleImpl class
ms.assetid: 971d82b7-a921-47fa-a4d8-909bed377ab0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8a5b3098961af4f3f9262cdc4c99dbe80b4ac7c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="idispeventsimpleimpl-class"></a>IDispEventSimpleImpl 類別
這個類別提供的實作`IDispatch`方法，而不從類型程式庫取得類型資訊。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <UINT nID, class T, const IID* pdiid>  
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```    
  
#### <a name="parameters"></a>參數  
 `nID`  
 來源物件的唯一識別碼。 當`IDispEventSimpleImpl`的基底類別的複合控制項，使用此參數包含所需的控制項的資源識別碼。 在其他情況下，使用任意的正整數。  
  
 `T`  
 使用者的類別，衍生自`IDispEventSimpleImpl`。  
  
 `pdiid`  
 這個類別所實作的事件分配程式介面的 IID 指標。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IDispEventSimpleImpl::Advise](#advise)|建立與預設的事件來源的連接。|  
|[IDispEventSimpleImpl::DispEventAdvise](#dispeventadvise)|建立事件來源的連接。|  
|[IDispEventSimpleImpl::DispEventUnadvise](#dispeventunadvise)|中斷與事件來源的連接。|  
|[IDispEventSimpleImpl::GetIDsOfNames](#getidsofnames)|傳回**E_NOTIMPL**。|  
|[IDispEventSimpleImpl::GetTypeInfo](#gettypeinfo)|傳回**E_NOTIMPL**。|  
|[IDispEventSimpleImpl::GetTypeInfoCount](#gettypeinfocount)|傳回**E_NOTIMPL**。|  
|[IDispEventSimpleImpl::Invoke](#invoke)|呼叫事件處理常式列在事件接收器對應。|  
|[IDispEventSimpleImpl::Unadvise](#unadvise)|中斷與的預設事件來源的連接。|  
  
## <a name="remarks"></a>備註  
 `IDispEventSimpleImpl`提供一種實作的事件分配程式介面，而不需要您提供每個方法/事件介面的實作程式碼。 `IDispEventSimpleImpl`提供的實作`IDispatch`方法。 您只需要提供您有興趣在處理事件的實作。  
  
 `IDispEventSimpleImpl`一起運作的事件接收對應至適當的處理常式函式的路由事件類別中。 若要使用此類別：  
  
-   新增[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)巨集，以您想要處理每個物件上的每個事件的事件接收對應。  
  
-   藉由傳遞指標到提供每個事件的型別資訊[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)結構做為每個項目的參數。 X86 平台，`_ATL_FUNC_INFO.cc`值必須 CC_CDECL 回呼函式呼叫的 __stdcall 方法。  
  
-   呼叫[DispEventAdvise](#dispeventadvise)之間建立連線的來源物件和基底類別。  
  
-   呼叫[DispEventUnadvise](#dispeventunadvise)中斷連線。  
  
 您必須衍生自`IDispEventSimpleImpl`(使用的唯一值`nID`) 針對每個您要處理事件的物件。 可以取消通知對一個來源物件針對不同的來源物件，然後通知重複使用的基底類別，但可以一次處理單一物件的來源物件的數目上限的數目受限於`IDispEventSimpleImpl`基底類別。  
  
 **IDispEventSimplImpl**提供的相同功能與[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)，只不過它不會從類型程式庫取得介面的類型資訊。 精靈會產生程式碼只根據`IDispEventImpl`，但是您可以使用`IDispEventSimpleImpl`以手動方式加入的程式碼。 使用`IDispEventSimpleImpl`當您尚未描述事件介面的類型程式庫，或想要避免與使用類型程式庫相關聯的額外負荷。  
  
> [!NOTE]
> `IDispEventImpl`和`IDispEventSimpleImpl`提供自己的實作**iunknown:: Queryinterface**啟用每個`IDispEventImpl`或`IDispEventSimpleImpl`基底類別做為個別的 COM 識別，同時，仍允許對類別成員的直接存取在您主要的 COM 物件。  
  
 CE ATL 實作 ActiveX 事件接收唯一支援的傳回值類型的 HRESULT 或 void，從您的事件處理常式方法。任何其他傳回值是不支援，且其行為未定義。  
  
 如需詳細資訊，請參閱[支援 IDispEventImpl](../../atl/supporting-idispeventimpl.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `_IDispEvent`  
  
 `_IDispEventLocator`  
  
 `IDispEventSimpleImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="advise"></a>IDispEventSimpleImpl::Advise  
 呼叫這個方法來建立與所代表的事件來源的連線*pUnk*。  
  
```
HRESULT Advise(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>參數  
 *pUnk*  
 [in]指標**IUnknown**事件來源物件的介面。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`任何失敗或`HRESULT`值。  
  
### <a name="remarks"></a>備註  
 從連線建立後，引發事件*pUnk*將會路由至您透過事件接收對應的類別中的處理常式。  
  
> [!NOTE]
>  如果您的類別衍生自多個`IDispEventSimpleImpl`類別，您必須明確呼叫此方法執行藉由範圍您感興趣的特定的基底類別的呼叫。  
  
 `Advise`建立的連接與預設的事件來源，它會取得的預設事件的來源物件由 IID [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface)。  
  
##  <a name="dispeventadvise"></a>IDispEventSimpleImpl::DispEventAdvise  
 呼叫這個方法來建立與所代表的事件來源的連線*pUnk*。  
  
```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```  
  
### <a name="parameters"></a>參數  
 *pUnk*  
 [in]指標**IUnknown**事件來源物件的介面。  
  
 `piid`  
 指向 IID 的事件來源物件指標。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`任何失敗或`HRESULT`值。  
  
### <a name="remarks"></a>備註  
 接著，從引發事件*pUnk*將會路由至您透過事件接收對應的類別中的處理常式。  
  
> [!NOTE]
>  如果您的類別衍生自多個`IDispEventSimpleImpl`類別，您必須明確呼叫此方法執行藉由範圍您感興趣的特定的基底類別的呼叫。  
  
 `DispEventAdvise`建立的連接中指定的事件來源與`pdiid`。  
  
##  <a name="dispeventunadvise"></a>IDispEventSimpleImpl::DispEventUnadvise  
 與所代表的事件來源會中斷連接*pUnk*。  
  
```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```  
  
### <a name="parameters"></a>參數  
 *pUnk*  
 [in]指標**IUnknown**事件來源物件的介面。  
  
 `piid`  
 指向 IID 的事件來源物件指標。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`任何失敗或`HRESULT`值。  
  
### <a name="remarks"></a>備註  
 中斷連接之後，事件就不會再路由至事件接收器對應中列出的處理常式函式。  
  
> [!NOTE]
>  如果您的類別衍生自多個`IDispEventSimpleImpl`類別，您必須明確呼叫此方法執行藉由範圍您感興趣的特定的基底類別的呼叫。  
  
 `DispEventAdvise`使用指定的事件來源所建立的連接會中斷`pdiid`。  
  
##  <a name="getidsofnames"></a>IDispEventSimpleImpl::GetIDsOfNames  
 這項實作**IDispatch::GetIDsOfNames**傳回**E_NOTIMPL**。  
  
```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IDispatch::GetIDsOfNames](http://msdn.microsoft.com/en-us/6f6cf233-3481-436e-8d6a-51f93bf91619) Windows SDK 中。  
  
##  <a name="gettypeinfo"></a>IDispEventSimpleImpl::GetTypeInfo  
 這項實作**IDispatch::GetTypeInfo**傳回**E_NOTIMPL**。  
  
```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IDispatch::GetTypeInfo](http://msdn.microsoft.com/en-us/cc1ec9aa-6c40-4e70-819c-a7c6dd6b8c99) Windows SDK 中。  
  
##  <a name="gettypeinfocount"></a>IDispEventSimpleImpl::GetTypeInfoCount  
 這項實作**IDispatch::GetTypeInfoCount**傳回**E_NOTIMPL**。  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IDispatch::GetTypeInfoCount](http://msdn.microsoft.com/en-us/da876d53-cb8a-465c-a43e-c0eb272e2a12) Windows SDK 中。  
  
##  <a name="invoke"></a>IDispEventSimpleImpl::Invoke  
 這項實作**idispatch:: Invoke**呼叫事件處理常式列出在事件接收器對應。  
  
```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID /* riid */,
    LCID lcid,
    WORD /* wFlags */,
    DISPPARMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* /* pexcepinfo */,
    UINT* /* puArgErr */);
```  
  
### <a name="remarks"></a>備註  
 請參閱[idispatch:: Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d)。  
  
##  <a name="unadvise"></a>IDispEventSimpleImpl::Unadvise  
 與所代表的事件來源會中斷連接*pUnk*。  
  
```
HRESULT Unadvise(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>參數  
 *pUnk*  
 [in]指標**IUnknown**事件來源物件的介面。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`任何失敗或`HRESULT`值。  
  
### <a name="remarks"></a>備註  
 中斷連接之後，事件就不會再路由至事件接收器對應中列出的處理常式函式。  
  
> [!NOTE]
>  如果您的類別衍生自多個`IDispEventSimpleImpl`類別，您必須明確呼叫此方法執行藉由範圍您感興趣的特定的基底類別的呼叫。  
  
 `Unadvise`使用指定的預設事件來源所建立的連接會中斷`pdiid`。  
  
 **Unavise**與預設的事件來源的連線中斷，它會取得的預設事件的來源物件由 IID [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface)。  
  
## <a name="see-also"></a>請參閱  
 [_ATL_FUNC_INFO 結構](../../atl/reference/atl-func-info-structure.md)   
 [IDispatchImpl 類別](../../atl/reference/idispatchimpl-class.md)   
 [IDispEventImpl 類別](../../atl/reference/idispeventimpl-class.md)   
 [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)   
 [類別概觀](../../atl/atl-class-overview.md)
