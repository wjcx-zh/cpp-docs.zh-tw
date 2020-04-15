---
title: IDispevent 簡單簡單課程
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
ms.openlocfilehash: 779e143094760c7bd868ad33f590f7fd8f004762
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329740"
---
# <a name="idispeventsimpleimpl-class"></a>IDispevent 簡單簡單課程

此類提供方法的實現,`IDispatch`而不從類型庫中獲取類型資訊。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <UINT nID, class T, const IID* pdiid>
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```

#### <a name="parameters"></a>參數

*nID*<br/>
源物件的唯一標識符。 當`IDispEventSimpleImpl`複合控制項的基類是時,使用此參數使用所需包含控制項的資源 ID。 在其他情況下,使用任意正整數。

*T*<br/>
使用者的類,派生自`IDispEventSimpleImpl`。

*皮迪德*<br/>
指向此類實現的事件不介面的IID的指標。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IDispEvent 簡單::建議](#advise)|建立與預設事件源的連接。|
|[IDispEvent 簡單::Dispevent建議](#dispeventadvise)|建立與事件源的連接。|
|[IDispEvent 簡單::Dispevent 無建議](#dispeventunadvise)|斷開與事件源的連接。|
|[IDispevent 簡單頁: :取得名稱](#getidsofnames)|返回E_NOTIMPL。|
|[IDispevent 簡單::獲取類型資訊](#gettypeinfo)|返回E_NOTIMPL。|
|[IDispevent 簡單::獲取類型資訊計數](#gettypeinfocount)|返回E_NOTIMPL。|
|[IDispevent 簡單::呼叫](#invoke)|呼叫事件接收器對應中列出的事件處理程式。|
|[IDispEvent 簡單::無建議](#unadvise)|斷開與預設事件源的連接。|

## <a name="remarks"></a>備註

`IDispEventSimpleImpl`提供了一種實現事件介面的方法,而無需為該介面上的每個方法/事件提供實現代碼。 `IDispEventSimpleImpl`提供了方法的`IDispatch`實現。 您只需為您感興趣的事件提供實現。

`IDispEventSimpleImpl`與類中的事件接收器映射結合使用,將事件路由到相應的處理程式函數。 要使用此類:

- 向要處理的每個物件上每個事件的事件向事件接收器映射添加[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)宏。

- 通過將指向[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)結構的指標作為參數傳遞給每個條目,從而為每個事件提供類型資訊。 在 x86 平臺`_ATL_FUNC_INFO.cc`上, 必須使用__stdcall回調函數調用方法CC_CDECL該值。

- 呼叫[DispEvent 建議](#dispeventadvise)以建立源物件和基類之間的連接。

- 致電[DispEventUn 建議](#dispeventunadvise)斷開連接。

您必須從`IDispEventSimpleImpl`(使用*nID*的唯一值 )派生出需要為其處理事件的每個物件。 可以通過對一個源物件取消建議來重用基類,然後針對不同的源物件提供建議,但一次由單個物件可以處理的最大源物件數受基類`IDispEventSimpleImpl`數的限制。

`IDispEventSimplImpl`提供與[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)相同的功能,只不過它不從類型庫中獲取有關介面的類型資訊。 嚮導僅基於`IDispEventImpl`生成代碼,但可以通過手動添加代碼`IDispEventSimpleImpl`來 使用。 當您`IDispEventSimpleImpl`沒有描述事件介面的類型庫或希望避免與使用類型庫關聯的開銷時,請使用。

> [!NOTE]
> `IDispEventImpl`並提供`IDispEventSimpleImpl`它們自己的實現`IUnknown::QueryInterface`,`IDispEventImpl`使`IDispEventSimpleImpl`每個或基項充當單獨的 COM 識別,同時仍然允許直接存取主 COM 物件中的類成員。

ActiveX 事件接收器的 CE ATL 實現僅支援事件處理程式方法中 HRESULT 類型的傳回值或 void;任何其他返回值不受支援,其行為未定義。

有關詳細資訊,請參閱支援[IDispEventImpl](../../atl/supporting-idispeventimpl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`_IDispEvent`

`_IDispEventLocator`

`IDispEventSimpleImpl`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="idispeventsimpleimpladvise"></a><a name="advise"></a>IDispEvent 簡單::建議

呼叫此方法以建立與*pUnk*表示的事件源的連接。

```
HRESULT Advise(IUnknown* pUnk);
```

### <a name="parameters"></a>參數

*龐克*<br/>
[在]指向事件源物件的`IUnknown`介面的指標。

### <a name="return-value"></a>傳回值

S_OK或任何故障 HRESULT 值。

### <a name="remarks"></a>備註

建立連接後,從*pUnk*觸發的事件將通過事件接收器映射路由到類中的處理程式。

> [!NOTE]
> 如果類派生自多個`IDispEventSimpleImpl`類,則需要通過將調用與感興趣的特定基類進行範圍界定來消除對此方法的歧義調用。

`Advise`建立與預設事件來源的連接,它獲取由[AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface)確定的物件的預設事件來源的 IID。

## <a name="idispeventsimpleimpldispeventadvise"></a><a name="dispeventadvise"></a>IDispEvent 簡單::Dispevent建議

呼叫此方法以建立與*pUnk*表示的事件源的連接。

```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>參數

*龐克*<br/>
[在]指向事件源物件的`IUnknown`介面的指標。

*皮伊德*<br/>
指向事件源物件的IID的指標。

### <a name="return-value"></a>傳回值

S_OK或任何故障 HRESULT 值。

### <a name="remarks"></a>備註

隨後,從*pUnk*觸發的事件將通過事件接收器映射路由到類中的處理程式。

> [!NOTE]
> 如果類派生自多個`IDispEventSimpleImpl`類,則需要通過將調用與感興趣的特定基類進行範圍界定來消除對此方法的歧義調用。

`DispEventAdvise`建立與`pdiid`中 指定的事件源的連接。

## <a name="idispeventsimpleimpldispeventunadvise"></a><a name="dispeventunadvise"></a>IDispEvent 簡單::Dispevent 無建議

斷開與*pUnk*表示的事件源的連接。

```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>參數

*龐克*<br/>
[在]指向事件源物件的`IUnknown`介面的指標。

*皮伊德*<br/>
指向事件源物件的IID的指標。

### <a name="return-value"></a>傳回值

S_OK或任何故障 HRESULT 值。

### <a name="remarks"></a>備註

連接斷開後,事件將不再路由到事件接收器映射中列出的處理程式函數。

> [!NOTE]
> 如果類派生自多個`IDispEventSimpleImpl`類,則需要通過將調用與感興趣的特定基類進行範圍界定來消除對此方法的歧義調用。

`DispEventAdvise`中斷與`pdiid`中 指定的事件源建立的連接。

## <a name="idispeventsimpleimplgetidsofnames"></a><a name="getidsofnames"></a>IDispevent 簡單頁: :取得名稱

返回的`IDispatch::GetIDsOfNames`這種實現E_NOTIMPL。

```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```

### <a name="remarks"></a>備註

請參閱[IDispatch:獲取](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames)Windows SDK 中的名稱。

## <a name="idispeventsimpleimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispevent 簡單::獲取類型資訊

返回的`IDispatch::GetTypeInfo`這種實現E_NOTIMPL。

```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```

### <a name="remarks"></a>備註

請參閱[IDispatch:在](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo)Windows SDK 中獲取類型資訊。

## <a name="idispeventsimpleimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispevent 簡單::獲取類型資訊計數

返回的`IDispatch::GetTypeInfoCount`這種實現E_NOTIMPL。

```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```

### <a name="remarks"></a>備註

請參考 IDispatch:在 Windows SDK 中[取得類型資訊 。](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount)

## <a name="idispeventsimpleimplinvoke"></a><a name="invoke"></a>IDispevent 簡單::呼叫

此實現`IDispatch::Invoke`調用事件接收器映射中列出的事件處理程式。

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

請參考[IDispatch::呼叫](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)。

## <a name="idispeventsimpleimplunadvise"></a><a name="unadvise"></a>IDispEvent 簡單::無建議

斷開與*pUnk*表示的事件源的連接。

```
HRESULT Unadvise(IUnknown* pUnk);
```

### <a name="parameters"></a>參數

*龐克*<br/>
[在]指向事件源物件的`IUnknown`介面的指標。

### <a name="return-value"></a>傳回值

S_OK或任何故障 HRESULT 值。

### <a name="remarks"></a>備註

連接斷開後,事件將不再路由到事件接收器映射中列出的處理程式函數。

> [!NOTE]
> 如果類派生自多個`IDispEventSimpleImpl`類,則需要通過將調用與感興趣的特定基類進行範圍界定來消除對此方法的歧義調用。

`Unadvise`中斷與`pdiid`中 指定的預設事件源建立的連接。

`Unavise`斷開與預設事件來源的連接,它獲取由[AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface)確定的物件的預設事件來源的 IID。

## <a name="see-also"></a>另請參閱

[_ATL_FUNC_INFO結構](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl 類別](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventImpl 類別](../../atl/reference/idispeventimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[類別概觀](../../atl/atl-class-overview.md)
