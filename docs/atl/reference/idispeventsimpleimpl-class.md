---
title: "IDispEventSimpleImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDispEventSimpleImpl
- ATL::IDispEventSimpleImpl
- ATL.IDispEventSimpleImpl
dev_langs:
- C++
helpviewer_keywords:
- IDispEventSimpleImpl class
ms.assetid: 971d82b7-a921-47fa-a4d8-909bed377ab0
caps.latest.revision: 27
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 6b7bc2c64139726f84f1c19c7d6b40e8d68cdc18
ms.lasthandoff: 02/24/2017

---
# <a name="idispeventsimpleimpl-class"></a>IDispEventSimpleImpl 類別
這個類別提供的實作`IDispatch`方法，而不需要從類型程式庫取得型別資訊。  
  
> [!IMPORTANT]
>  這個類別及其成員無法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式內使用。  
  
## <a name="syntax"></a>語法  
  
```
template <UINT nID, class T, const IID* pdiid>  
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```    
  
#### <a name="parameters"></a>參數  
 `nID`  
 來源物件的唯一識別項。 當`IDispEventSimpleImpl`是基底類別對於複合控制項，內含的控制項所需的資源識別碼，將這個參數。 在其他情況下，使用任意的正整數值。  
  
 `T`  
 使用者的類別，衍生自`IDispEventSimpleImpl`。  
  
 `pdiid`  
 這個類別所實作的事件分配介面的 IID 指標。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[IDispEventSimpleImpl::Advise](#advise)|建立與預設的事件來源的連接。|  
|[IDispEventSimpleImpl::DispEventAdvise](#dispeventadvise)|建立事件來源的連接。|  
|[IDispEventSimpleImpl::DispEventUnadvise](#dispeventunadvise)|中斷與事件來源的連接。|  
|[IDispEventSimpleImpl::GetIDsOfNames](#getidsofnames)|傳回**E_NOTIMPL**。|  
|[IDispEventSimpleImpl::GetTypeInfo](#gettypeinfo)|傳回**E_NOTIMPL**。|  
|[IDispEventSimpleImpl::GetTypeInfoCount](#gettypeinfocount)|傳回**E_NOTIMPL**。|  
|[IDispEventSimpleImpl::Invoke](#invoke)|呼叫事件處理常式列在事件接收對應。|  
|[IDispEventSimpleImpl::Unadvise](#unadvise)|中斷與預設事件來源的連接。|  
  
## <a name="remarks"></a>備註  
 `IDispEventSimpleImpl`提供一種實作事件分配程式介面，而不需要您提供每個方法/事件介面的實作程式碼。 `IDispEventSimpleImpl`提供的實作`IDispatch`方法。 您只需要提供您所需處理事件的實作。  
  
 `IDispEventSimpleImpl`可搭配[事件接收對應](http://msdn.microsoft.com/library/32542b3d-ac43-4139-8ac4-41c48481744f)路由至適當的處理常式函式的事件類別中。 若要使用這個類別︰  
  
-   新增[SINK_ENTRY_INFO](http://msdn.microsoft.com/library/1a0ae260-2c82-4926-a537-db01e5f206a7)巨集，以您想要處理每個物件上的每個事件的事件接收對應。  
  
-   藉由傳遞的指標，提供每個事件的型別資訊[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)結構做為參數，每個項目。 在 x86 平台，`_ATL_FUNC_INFO.cc`值必須是 CC_CDECL 以回呼函數呼叫 __stdcall 的方法。  
  
-   呼叫[DispEventAdvise](#dispeventadvise)之間建立連線的來源物件和基底類別。  
  
-   呼叫[DispEventUnadvise](#dispeventunadvise)中斷連線。  
  
 您必須衍生自`IDispEventSimpleImpl`(使用的唯一值`nID`) 針對每個您要處理事件的物件。 可以對一個來源物件針對不同的來源物件，然後通知取消通知重複使用的基底類別，但可以一次處理單一物件的來源物件的數目上限受限於數目`IDispEventSimpleImpl`基底類別。  
  
 **IDispEventSimplImpl**提供相同的功能[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)，但它不會從類型程式庫取得介面的型別資訊。 精靈產生程式碼只有在基礎`IDispEventImpl`，但是您可以使用`IDispEventSimpleImpl`以手動方式加入的程式碼。 使用`IDispEventSimpleImpl`當您沒有描述事件介面的型別程式庫或想要避免使用型別程式庫相關聯的額外負荷。  
  
> [!NOTE]
> `IDispEventImpl`和`IDispEventSimpleImpl`提供自己的實作**Iid**啟用每個`IDispEventImpl`或`IDispEventSimpleImpl`基底類別做為個別的 COM 身分識別，同時仍允許對類別成員的直接存取主要的 COM 物件中。  
  
 CE ATL 實作 ActiveX 事件接收唯一支援的傳回值型別 HRESULT 或 void 從您的事件處理常式方法。任何傳回的值不受支援，且其行為未定義。  
  
 如需詳細資訊，請參閱[支援 IDispEventImpl](../../atl/supporting-idispeventimpl.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `_IDispEvent`  
  
 `_IDispEventLocator`  
  
 `IDispEventSimpleImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="a-nameadvisea--idispeventsimpleimpladvise"></a><a name="advise"></a>IDispEventSimpleImpl::Advise  
 呼叫這個方法來建立與所代表的事件來源的連接*pUnk*。  
  
```
HRESULT Advise(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>參數  
 *pUnk*  
 [in]指標**IUnknown**事件來源物件的介面。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`任何失敗或`HRESULT`值。  
  
### <a name="remarks"></a>備註  
 一旦建立連線之後，從引發事件*pUnk*將會路由至您透過事件接收對應的類別中的處理常式。  
  
> [!NOTE]
>  如果您的類別衍生自多個`IDispEventSimpleImpl`類別，您必須明確執行呼叫此方法設定特定的基底類別呼叫您感興趣的範圍。  
  
 `Advise`建立的連線與預設的事件來源，它會取得物件所決定的預設事件來源的 IID [AtlGetObjectSourceInterface](http://msdn.microsoft.com/library/a8528f45-fbfb-4e24-ad1a-1d69b2897155)。  
  
##  <a name="a-namedispeventadvisea--idispeventsimpleimpldispeventadvise"></a><a name="dispeventadvise"></a>IDispEventSimpleImpl::DispEventAdvise  
 呼叫這個方法來建立與所代表的事件來源的連接*pUnk*。  
  
```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```  
  
### <a name="parameters"></a>參數  
 *pUnk*  
 [in]指標**IUnknown**事件來源物件的介面。  
  
 `piid`  
 IID 事件來源物件的指標。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`任何失敗或`HRESULT`值。  
  
### <a name="remarks"></a>備註  
 接著，從引發事件*pUnk*將會路由至您透過事件接收對應的類別中的處理常式。  
  
> [!NOTE]
>  如果您的類別衍生自多個`IDispEventSimpleImpl`類別，您必須明確執行呼叫此方法設定特定的基底類別呼叫您感興趣的範圍。  
  
 `DispEventAdvise`建立連接中指定的事件來源與`pdiid`。  
  
##  <a name="a-namedispeventunadvisea--idispeventsimpleimpldispeventunadvise"></a><a name="dispeventunadvise"></a>IDispEventSimpleImpl::DispEventUnadvise  
 與所代表的事件來源將會中斷連接*pUnk*。  
  
```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```  
  
### <a name="parameters"></a>參數  
 *pUnk*  
 [in]指標**IUnknown**事件來源物件的介面。  
  
 `piid`  
 IID 事件來源物件的指標。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`任何失敗或`HRESULT`值。  
  
### <a name="remarks"></a>備註  
 中斷連接之後，事件將不會再路由至事件接收對應所列出的處理常式函數。  
  
> [!NOTE]
>  如果您的類別衍生自多個`IDispEventSimpleImpl`類別，您必須明確執行呼叫此方法設定特定的基底類別呼叫您感興趣的範圍。  
  
 `DispEventAdvise`已建立與指定的事件來源的連接會中斷`pdiid`。  
  
##  <a name="a-namegetidsofnamesa--idispeventsimpleimplgetidsofnames"></a><a name="getidsofnames"></a>IDispEventSimpleImpl::GetIDsOfNames  
 這項實作的**IDispatch::GetIDsOfNames**傳回**E_NOTIMPL**。  
  
```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IDispatch::GetIDsOfNames](http://msdn.microsoft.com/en-us/6f6cf233-3481-436e-8d6a-51f93bf91619)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegettypeinfoa--idispeventsimpleimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispEventSimpleImpl::GetTypeInfo  
 這項實作的**IDispatch::GetTypeInfo**傳回**E_NOTIMPL**。  
  
```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IDispatch::GetTypeInfo](http://msdn.microsoft.com/en-us/cc1ec9aa-6c40-4e70-819c-a7c6dd6b8c99)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegettypeinfocounta--idispeventsimpleimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispEventSimpleImpl::GetTypeInfoCount  
 這項實作的**IDispatch::GetTypeInfoCount**傳回**E_NOTIMPL**。  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IDispatch::GetTypeInfoCount](http://msdn.microsoft.com/en-us/da876d53-cb8a-465c-a43e-c0eb272e2a12)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameinvokea--idispeventsimpleimplinvoke"></a><a name="invoke"></a>IDispEventSimpleImpl::Invoke  
 這項實作的**Excepinfo**呼叫事件處理常式列出的事件接收對應。  
  
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
 請參閱[Excepinfo](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d)。  
  
##  <a name="a-nameunadvisea--idispeventsimpleimplunadvise"></a><a name="unadvise"></a>IDispEventSimpleImpl::Unadvise  
 與所代表的事件來源將會中斷連接*pUnk*。  
  
```
HRESULT Unadvise(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>參數  
 *pUnk*  
 [in]指標**IUnknown**事件來源物件的介面。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`任何失敗或`HRESULT`值。  
  
### <a name="remarks"></a>備註  
 中斷連接之後，事件將不會再路由至事件接收對應所列出的處理常式函數。  
  
> [!NOTE]
>  如果您的類別衍生自多個`IDispEventSimpleImpl`類別，您必須明確執行呼叫此方法設定特定的基底類別呼叫您感興趣的範圍。  
  
 `Unadvise`中指定的預設事件來源與已建立的連線會中斷`pdiid`。  
  
 **Unavise**與預設的事件來源的連線中斷，它會取得物件所決定的預設事件來源的 IID [AtlGetObjectSourceInterface](http://msdn.microsoft.com/library/a8528f45-fbfb-4e24-ad1a-1d69b2897155)。  
  
## <a name="see-also"></a>另請參閱  
 [_ATL_FUNC_INFO 結構](../../atl/reference/atl-func-info-structure.md)   
 [IDispatchImpl 類別](../../atl/reference/idispatchimpl-class.md)   
 [IDispEventImpl 類別](../../atl/reference/idispeventimpl-class.md)   
 [SINK_ENTRY_INFO](http://msdn.microsoft.com/library/1a0ae260-2c82-4926-a537-db01e5f206a7)   
 [類別概觀](../../atl/atl-class-overview.md)

