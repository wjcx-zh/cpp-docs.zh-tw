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
ms.openlocfilehash: 3ceb436e4f20a17ecd086fb68f9c1cfdcbe0be3e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864720"
---
# <a name="idispeventsimpleimpl-class"></a>IDispEventSimpleImpl 類別

這個類別會提供 `IDispatch` 方法的執行，而不需要從類型程式庫取得類型資訊。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <UINT nID, class T, const IID* pdiid>
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```

#### <a name="parameters"></a>參數

*nID*<br/>
來源物件的唯一識別碼。 當 `IDispEventSimpleImpl` 是複合控制項的基類時，請使用此參數所需包含控制項的資源識別碼。 在其他情況下，請使用任意正整數。

*T*<br/>
使用者的類別，衍生自 `IDispEventSimpleImpl`。

*pdiid*<br/>
這個類別所執行之事件分配介面的 IID 指標。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IDispEventSimpleImpl：： Advise](#advise)|建立與預設事件來源的連接。|
|[IDispEventSimpleImpl：:D ispEventAdvise](#dispeventadvise)|建立與事件來源的連接。|
|[IDispEventSimpleImpl：:D ispEventUnadvise](#dispeventunadvise)|中斷與事件來源的連接。|
|[IDispEventSimpleImpl：： GetIDsOfNames](#getidsofnames)|傳回 E_NOTIMPL。|
|[IDispEventSimpleImpl：： GetTypeInfo](#gettypeinfo)|傳回 E_NOTIMPL。|
|[IDispEventSimpleImpl：： GetTypeInfoCount](#gettypeinfocount)|傳回 E_NOTIMPL。|
|[IDispEventSimpleImpl：： Invoke](#invoke)|呼叫事件接收器對應中列出的事件處理常式。|
|[IDispEventSimpleImpl：： Unadvise](#unadvise)|中斷與預設事件來源的連接。|

## <a name="remarks"></a>備註

`IDispEventSimpleImpl` 提供一種方式來執行事件分配介面，而不需要您為該介面上的每個方法/事件提供實程式程式碼。 `IDispEventSimpleImpl` 提供 `IDispatch` 方法的執行。 您只需要提供您想要處理之事件的「執行」。

`IDispEventSimpleImpl` 與類別中的事件接收器對應搭配運作，以將事件路由至適當的處理函式。 若要使用此類別：

- 針對您要處理之每個物件上的每個事件，將[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)宏新增至事件接收對應。

- 藉由將[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)結構的指標當做參數傳遞至每個專案，以提供每個事件的類型資訊。 在 x86 平臺上，`_ATL_FUNC_INFO.cc` 的值必須 CC_CDECL 回呼函數呼叫 __stdcall 的方法。

- 呼叫[DispEventAdvise](#dispeventadvise)以建立來源物件與基類之間的連接。

- 呼叫[DispEventUnadvise](#dispeventunadvise)以中斷連接。

您必須針對需要處理事件的每個物件，從 `IDispEventSimpleImpl` （針對*nID*使用唯一值）衍生。 您可以針對某個來源物件 unadvising 重複使用基類，然後針對不同的來源物件進行建議，但是單一物件可一次處理的最大來源物件數目會受到 `IDispEventSimpleImpl` 的基類數目所限制。

`IDispEventSimplImpl` 提供與[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)相同的功能，但它不會從類型程式庫取得介面的類型資訊。 這些程式只會根據 `IDispEventImpl`來產生程式碼，但您可以手動新增程式碼來使用 `IDispEventSimpleImpl`。 當您沒有描述事件介面的類型程式庫，或想要避免與使用類型程式庫相關聯的額外負荷時，請使用 `IDispEventSimpleImpl`。

> [!NOTE]
> `IDispEventImpl` 和 `IDispEventSimpleImpl` 提供自己的 `IUnknown::QueryInterface`，讓每個 `IDispEventImpl` 或 `IDispEventSimpleImpl` 基類作為個別的 COM 身分識別，同時仍允許直接存取主要 COM 物件中的類別成員。

適用于 ActiveX 事件接收的 CE ATL 實作為，只支援事件處理常式方法中 HRESULT 或 void 類型的傳回值;不支援任何其他傳回值，且其行為未定義。

如需詳細資訊，請參閱[支援 IDispEventImpl](../../atl/supporting-idispeventimpl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`_IDispEvent`

`_IDispEventLocator`

`IDispEventSimpleImpl`

## <a name="requirements"></a>需求

**標頭：** atlcom.h。h

##  <a name="advise"></a>IDispEventSimpleImpl：： Advise

呼叫這個方法，以建立與*pUnk*所代表之事件來源的連接。

```
HRESULT Advise(IUnknown* pUnk);
```

### <a name="parameters"></a>參數

*pUnk*<br/>
在事件來源物件之 `IUnknown` 介面的指標。

### <a name="return-value"></a>傳回值

S_OK 或任何失敗的 HRESULT 值。

### <a name="remarks"></a>備註

一旦建立連接，從*pUnk*引發的事件就會透過事件接收對應路由至您類別中的處理常式。

> [!NOTE]
>  如果您的類別衍生自多個 `IDispEventSimpleImpl` 類別，您必須將呼叫的範圍設定為您感興趣的特定基類，藉此區分對此方法的呼叫。

`Advise` 會建立與預設事件來源的連線，它會取得物件預設事件來源的 IID （由[AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface)決定）。

##  <a name="dispeventadvise"></a>IDispEventSimpleImpl：:D ispEventAdvise

呼叫這個方法，以建立與*pUnk*所代表之事件來源的連接。

```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>參數

*pUnk*<br/>
在事件來源物件之 `IUnknown` 介面的指標。

*piid*<br/>
事件來源物件之 IID 的指標。

### <a name="return-value"></a>傳回值

S_OK 或任何失敗的 HRESULT 值。

### <a name="remarks"></a>備註

之後，從*pUnk*引發的事件會透過事件接收對應，路由至您類別中的處理常式。

> [!NOTE]
>  如果您的類別衍生自多個 `IDispEventSimpleImpl` 類別，您必須將呼叫的範圍設定為您感興趣的特定基類，藉此區分對此方法的呼叫。

`DispEventAdvise` 會使用 `pdiid`中指定的事件來源來建立連接。

##  <a name="dispeventunadvise"></a>IDispEventSimpleImpl：:D ispEventUnadvise

中斷連接與*pUnk*所代表的事件來源。

```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>參數

*pUnk*<br/>
在事件來源物件之 `IUnknown` 介面的指標。

*piid*<br/>
事件來源物件之 IID 的指標。

### <a name="return-value"></a>傳回值

S_OK 或任何失敗的 HRESULT 值。

### <a name="remarks"></a>備註

連接中斷之後，事件就不會再路由至事件接收器對應中所列的處理常式函式。

> [!NOTE]
>  如果您的類別衍生自多個 `IDispEventSimpleImpl` 類別，您必須將呼叫的範圍設定為您感興趣的特定基類，藉此區分對此方法的呼叫。

`DispEventAdvise` 中斷與 `pdiid`中指定的事件來源建立的連接。

##  <a name="getidsofnames"></a>IDispEventSimpleImpl：： GetIDsOfNames

這個 `IDispatch::GetIDsOfNames` 的執行會傳回 E_NOTIMPL。

```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IDispatch：： GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) 。

##  <a name="gettypeinfo"></a>IDispEventSimpleImpl：： GetTypeInfo

這個 `IDispatch::GetTypeInfo` 的執行會傳回 E_NOTIMPL。

```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IDispatch：： GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) 。

##  <a name="gettypeinfocount"></a>IDispEventSimpleImpl：： GetTypeInfoCount

這個 `IDispatch::GetTypeInfoCount` 的執行會傳回 E_NOTIMPL。

```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IDispatch：： GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) 。

##  <a name="invoke"></a>IDispEventSimpleImpl：： Invoke

這個 `IDispatch::Invoke` 的執行會呼叫事件接收器對應中所列的事件處理常式。

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

請參閱[IDispatch：： Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)。

##  <a name="unadvise"></a>IDispEventSimpleImpl：： Unadvise

中斷連接與*pUnk*所代表的事件來源。

```
HRESULT Unadvise(IUnknown* pUnk);
```

### <a name="parameters"></a>參數

*pUnk*<br/>
在事件來源物件之 `IUnknown` 介面的指標。

### <a name="return-value"></a>傳回值

S_OK 或任何失敗的 HRESULT 值。

### <a name="remarks"></a>備註

連接中斷之後，事件就不會再路由至事件接收器對應中所列的處理常式函式。

> [!NOTE]
>  如果您的類別衍生自多個 `IDispEventSimpleImpl` 類別，您必須將呼叫的範圍設定為您感興趣的特定基類，藉此區分對此方法的呼叫。

`Unadvise` 會中斷以 `pdiid`中指定之預設事件來源建立的連接。

`Unavise` 中斷與預設事件來源的連接，它會取得物件的預設事件來源 IID，如[AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface)所決定。

## <a name="see-also"></a>另請參閱

[_ATL_FUNC_INFO 結構](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl 類別](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventImpl 類別](../../atl/reference/idispeventimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[類別總覽](../../atl/atl-class-overview.md)
