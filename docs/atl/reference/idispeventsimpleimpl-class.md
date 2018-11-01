---
title: IDispEventSimpleImpl 類別
ms.date: 11/04/2016
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
helpviewer_keywords:
- IDispEventSimpleImpl class
ms.assetid: 971d82b7-a921-47fa-a4d8-909bed377ab0
ms.openlocfilehash: a0be64cca6725c0ad0852752e6c6c440377c9e7a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447901"
---
# <a name="idispeventsimpleimpl-class"></a>IDispEventSimpleImpl 類別

這個類別提供的實作`IDispatch`方法，而不需要從類型程式庫中取得類型資訊。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template <UINT nID, class T, const IID* pdiid>
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```

#### <a name="parameters"></a>參數

*nID*<br/>
來源物件的唯一識別碼。 當`IDispEventSimpleImpl`的基底類別為複合控制項，使用此參數所需的自主控制的資源識別碼。 在其他情況下，使用任意的正整數。

*T*<br/>
使用者的類別，衍生自`IDispEventSimpleImpl`。

*pdiid*<br/>
要由此類別實作的事件分配程式介面的 IID 的指標。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IDispEventSimpleImpl::Advise](#advise)|建立使用預設的事件來源的連線。|
|[IDispEventSimpleImpl::DispEventAdvise](#dispeventadvise)|建立事件來源的連線。|
|[IDispEventSimpleImpl::DispEventUnadvise](#dispeventunadvise)|中斷與事件來源的連接。|
|[IDispEventSimpleImpl::GetIDsOfNames](#getidsofnames)|傳回 E_NOTIMPL。|
|[IDispEventSimpleImpl::GetTypeInfo](#gettypeinfo)|傳回 E_NOTIMPL。|
|[IDispEventSimpleImpl::GetTypeInfoCount](#gettypeinfocount)|傳回 E_NOTIMPL。|
|[IDispEventSimpleImpl::Invoke](#invoke)|呼叫事件處理常式則會列在事件接收對應中。|
|[IDispEventSimpleImpl::Unadvise](#unadvise)|中斷與預設的事件來源的連接。|

## <a name="remarks"></a>備註

`IDispEventSimpleImpl` 提供實作事件分配程式介面，而不需要您的方式，提供每個方法/事件上該介面的實作程式碼。 `IDispEventSimpleImpl` 提供的實作`IDispatch`方法。 您只需要提供您感興趣處理事件的實作。

`IDispEventSimpleImpl` 適用於搭配事件接收對應，在您的類別，以將事件路由至適當的處理常式函式。 若要使用此類別：

- 新增[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)針對每個您想要處理的物件上的每個事件的事件接收對應的巨集。

- 藉由傳遞的指標，提供每個事件的型別資訊[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)結構做為參數，每個項目。 在 x86 平台，`_ATL_FUNC_INFO.cc`值必須是 CC_CDECL 與回呼函式呼叫的 __stdcall 方法。

- 呼叫[DispEventAdvise](#dispeventadvise)以建立來源物件與基底類別之間的連線。

- 呼叫[DispEventUnadvise](#dispeventunadvise)中斷連線。

您必須衍生自`IDispEventSimpleImpl`(使用的唯一值*nID*) 針對每個您要處理事件的物件。 您可以藉由取消通知對一個來源物件，則建議針對不同的來源物件，重複使用的基底類別，但可由單一物件一次的來源物件的數目上限的數目受限於`IDispEventSimpleImpl`基底類別。

`IDispEventSimplImpl` 提供與相同的功能[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)，但它不會從類型程式庫中取得有關介面的型別資訊。 精靈會產生程式碼只根據`IDispEventImpl`，但您可以使用`IDispEventSimpleImpl`以手動方式加入的程式碼。 使用`IDispEventSimpleImpl`當您尚未描述事件介面的型別程式庫，或想要避免與使用類型程式庫相關聯的額外負荷。

> [!NOTE]
> `IDispEventImpl` 並`IDispEventSimpleImpl`提供其自己實作的`IUnknown::QueryInterface`啟用每個`IDispEventImpl`或`IDispEventSimpleImpl`基底類別，作為個別的 COM 識別，同時仍然允許對類別成員的直接存取，您主要的 COM 物件中。

CE ATL 實作 ActiveX 事件接收器只支援傳回值的型別 HRESULT 或 void，從您的事件處理常式方法;任何傳回的值不受支援，且其行為未定義。

如需詳細資訊，請參閱 <<c0> [ 支援 IDispEventImpl](../../atl/supporting-idispeventimpl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`_IDispEvent`

`_IDispEventLocator`

`IDispEventSimpleImpl`

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="advise"></a>  IDispEventSimpleImpl::Advise

呼叫這個方法來建立與所代表的事件來源的連線*pUnk*。

```
HRESULT Advise(IUnknown* pUnk);
```

### <a name="parameters"></a>參數

*pUnk*<br/>
[in]指標`IUnknown`事件來源物件的介面。

### <a name="return-value"></a>傳回值

S_OK 或任何失敗 HRESULT 值。

### <a name="remarks"></a>備註

一旦建立連線之後，從引發事件*pUnk*將會路由至您的類別，透過事件接收對應中的處理常式。

> [!NOTE]
>  如果您的類別衍生自多個`IDispEventSimpleImpl`類別，您必須明確呼叫此方法執行的範圍限定您感興趣的特定的基底類別的呼叫。

`Advise` 建立連線使用預設的事件來源，它會取得預設事件來源的物件由 IID [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface)。

##  <a name="dispeventadvise"></a>  IDispEventSimpleImpl::DispEventAdvise

呼叫這個方法來建立與所代表的事件來源的連線*pUnk*。

```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>參數

*pUnk*<br/>
[in]指標`IUnknown`事件來源物件的介面。

*piid*<br/>
IID 事件來源物件的指標。

### <a name="return-value"></a>傳回值

S_OK 或任何失敗 HRESULT 值。

### <a name="remarks"></a>備註

接著，從引發事件*pUnk*將會路由至您的類別，透過事件接收對應中的處理常式。

> [!NOTE]
>  如果您的類別衍生自多個`IDispEventSimpleImpl`類別，您必須明確呼叫此方法執行的範圍限定您感興趣的特定的基底類別的呼叫。

`DispEventAdvise` 建立連接中指定的事件來源與`pdiid`。

##  <a name="dispeventunadvise"></a>  IDispEventSimpleImpl::DispEventUnadvise

使用所代表的事件來源將會中斷連接*pUnk*。

```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>參數

*pUnk*<br/>
[in]指標`IUnknown`事件來源物件的介面。

*piid*<br/>
IID 事件來源物件的指標。

### <a name="return-value"></a>傳回值

S_OK 或任何失敗 HRESULT 值。

### <a name="remarks"></a>備註

中斷連接之後，事件將不會再被路由傳送至事件接收對應中所列的處理常式函式。

> [!NOTE]
>  如果您的類別衍生自多個`IDispEventSimpleImpl`類別，您必須明確呼叫此方法執行的範圍限定您感興趣的特定的基底類別的呼叫。

`DispEventAdvise` 使用中指定的事件來源所建立的連接會中斷`pdiid`。

##  <a name="getidsofnames"></a>  IDispEventSimpleImpl::GetIDsOfNames

這個實作`IDispatch::GetIDsOfNames`傳回 E_NOTIMPL。

```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```

### <a name="remarks"></a>備註

請參閱[IDispatch::GetIDsOfNames](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-getidsofnames) Windows SDK 中。

##  <a name="gettypeinfo"></a>  IDispEventSimpleImpl::GetTypeInfo

這個實作`IDispatch::GetTypeInfo`傳回 E_NOTIMPL。

```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```

### <a name="remarks"></a>備註

請參閱[IDispatch::GetTypeInfo](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfo) Windows SDK 中。

##  <a name="gettypeinfocount"></a>  IDispEventSimpleImpl::GetTypeInfoCount

這個實作`IDispatch::GetTypeInfoCount`傳回 E_NOTIMPL。

```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```

### <a name="remarks"></a>備註

請參閱[IDispatch::GetTypeInfoCount](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) Windows SDK 中。

##  <a name="invoke"></a>  IDispEventSimpleImpl::Invoke

這個實作`IDispatch::Invoke`事件處理常式列出在事件接收對應的呼叫。

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

請參閱[idispatch:: Invoke](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke)。

##  <a name="unadvise"></a>  IDispEventSimpleImpl::Unadvise

使用所代表的事件來源將會中斷連接*pUnk*。

```
HRESULT Unadvise(IUnknown* pUnk);
```

### <a name="parameters"></a>參數

*pUnk*<br/>
[in]指標`IUnknown`事件來源物件的介面。

### <a name="return-value"></a>傳回值

S_OK 或任何失敗 HRESULT 值。

### <a name="remarks"></a>備註

中斷連接之後，事件將不會再被路由傳送至事件接收對應中所列的處理常式函式。

> [!NOTE]
>  如果您的類別衍生自多個`IDispEventSimpleImpl`類別，您必須明確呼叫此方法執行的範圍限定您感興趣的特定的基底類別的呼叫。

`Unadvise` 使用中指定的預設事件來源所建立的連接會中斷`pdiid`。

`Unavise` 使用預設的事件來源的連線中斷，它會取得預設事件來源的物件由 IID [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface)。

## <a name="see-also"></a>另請參閱

[_ATL_FUNC_INFO 結構](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl 類別](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventImpl 類別](../../atl/reference/idispeventimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[類別概觀](../../atl/atl-class-overview.md)
