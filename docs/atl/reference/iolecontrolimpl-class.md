---
title: IOleControlImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IOleControlImpl
- ATLCTL/ATL::IOleControlImpl
- ATLCTL/ATL::IOleControlImpl::FreezeEvents
- ATLCTL/ATL::IOleControlImpl::GetControlInfo
- ATLCTL/ATL::IOleControlImpl::OnAmbientPropertyChange
- ATLCTL/ATL::IOleControlImpl::OnMnemonic
helpviewer_keywords:
- IOleControlImpl class
ms.assetid: 5a4255ad-ede4-49ca-ba9a-07c2e919fa85
ms.openlocfilehash: 3bdb501d8210c98ce982719358564c4937991e12
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864945"
---
# <a name="iolecontrolimpl-class"></a>IOleControlImpl 類別

這個類別會提供 `IOleControl` 介面的預設執行，並實 `IUnknown`。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class IOleControlImpl
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自 `IOleControlImpl`的類別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IOleControlImpl::FreezeEvents](#freezeevents)|指出容器是否忽略或接受來自控制項的事件。|
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|填入控制項鍵盤行為的相關資訊。 ATL 執行會傳回 E_NOTIMPL。|
|[IOleControlImpl：： OnAmbientPropertyChange](#onambientpropertychange)|通知控制項，其中一個或多個容器的環境屬性已變更。 ATL 執行會傳回 S_OK。|
|[IOleControlImpl::OnMnemonic](#onmnemonic)|通知控制項使用者已按下指定的按鍵。 ATL 執行會傳回 E_NOTIMPL。|

## <a name="remarks"></a>備註

類別 `IOleControlImpl` 會提供[IOleControl](/windows/win32/api/ocidl/nn-ocidl-iolecontrol)介面的預設執行，並在偵錯工具中將資訊傳送至傾印裝置，藉以實 `IUnknown`。

**相關文章** [atl 教學](../../atl/active-template-library-atl-tutorial.md)課程，[建立 atl 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層

`IOleControl`

`IOleControlImpl`

## <a name="requirements"></a>需求

**標頭：** atlctl。h

##  <a name="freezeevents"></a>IOleControlImpl::FreezeEvents

在 ATL 的執行中，如果 `bFreeze` 為 TRUE，`FreezeEvents` 會遞增控制項類別的 `m_nFreezeEvents` 資料成員，而如果 `bFreeze` 為 FALSE，則會遞減 `m_nFreezeEvents`。

```
HRESULT FreezeEvents(BOOL bFreeze);
```

### <a name="remarks"></a>備註

`FreezeEvents` 接著會傳回 S_OK。

請參閱 Windows SDK 中的[IOleControl：： FreezeEvents](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-freezeevents) 。

##  <a name="getcontrolinfo"></a>IOleControlImpl::GetControlInfo

填入控制項鍵盤行為的相關資訊。

```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleControl： GetControlInfo](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-getcontrolinfo) 。

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

##  <a name="onambientpropertychange"></a>IOleControlImpl：： OnAmbientPropertyChange

通知控制項，其中一個或多個容器的環境屬性已變更。

```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleControl：： OnAmbientPropertyChange](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onambientpropertychange) 。

##  <a name="onmnemonic"></a>IOleControlImpl::OnMnemonic

通知控制項使用者已按下指定的按鍵。

```
HRESULT OnMnemonic(LPMSG pMsg);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleControl：： OnMnemonic](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onmnemonic) 。

## <a name="see-also"></a>另請參閱

[IOleObjectImpl 類別](../../atl/reference/ioleobjectimpl-class.md)<br/>
[ActiveX 控制項介面](/windows/win32/com/activex-controls-interfaces)<br/>
[類別總覽](../../atl/atl-class-overview.md)
