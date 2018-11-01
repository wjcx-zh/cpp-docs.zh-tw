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
ms.openlocfilehash: 8b84f982d06547dd162da530d326d4cdb92e254a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442155"
---
# <a name="iolecontrolimpl-class"></a>IOleControlImpl 類別

這個類別提供的預設實作`IOleControl`介面和實作`IUnknown`。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template<class T>
class IOleControlImpl
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類別，衍生自`IOleControlImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IOleControlImpl::FreezeEvents](#freezeevents)|指出容器會忽略，或接受來自控制項的事件。|
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|會填滿控制項的鍵盤行為的相關資訊。 ATL 實作會傳回 E_NOTIMPL。|
|[IOleControlImpl::OnAmbientPropertyChange](#onambientpropertychange)|通知控制項已變更一或多個容器的環境屬性。 ATL 實作會傳回 S_OK。|
|[IOleControlImpl::OnMnemonic](#onmnemonic)|通知使用者已按下指定的按鍵輸入的控制項。 ATL 實作會傳回 E_NOTIMPL。|

## <a name="remarks"></a>備註

類別`IOleControlImpl`提供的預設實作[IOleControl](/windows/desktop/api/ocidl/nn-ocidl-iolecontrol)介面和實作`IUnknown`資訊傳送給傾印裝置在偵錯組建。

**相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層

`IOleControl`

`IOleControlImpl`

## <a name="requirements"></a>需求

**標頭：** atlctl.h

##  <a name="freezeevents"></a>  IOleControlImpl::FreezeEvents

在 ATL 的實作中，`FreezeEvents`遞增控制項類別的`m_nFreezeEvents`資料成員若`bFreeze`為 TRUE，並遞減`m_nFreezeEvents`如果`bFreeze`為 FALSE。

```
HRESULT FreezeEvents(BOOL bFreeze);
```

### <a name="remarks"></a>備註

`FreezeEvents` 接著會傳回 S_OK。

請參閱[IOleControl::FreezeEvents](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-freezeevents) Windows SDK 中。

##  <a name="getcontrolinfo"></a>  IOleControlImpl::GetControlInfo

會填滿控制項的鍵盤行為的相關資訊。

```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```

### <a name="remarks"></a>備註

請參閱[IOleControl:GetControlInfo](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-getcontrolinfo) Windows SDK 中。

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

##  <a name="onambientpropertychange"></a>  IOleControlImpl::OnAmbientPropertyChange

通知控制項已變更一或多個容器的環境屬性。

```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

請參閱[IOleControl::OnAmbientPropertyChange](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-onambientpropertychange) Windows SDK 中。

##  <a name="onmnemonic"></a>  IOleControlImpl::OnMnemonic

通知使用者已按下指定的按鍵輸入的控制項。

```
HRESULT OnMnemonic(LPMSG pMsg);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱[IOleControl::OnMnemonic](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-onmnemonic) Windows SDK 中。

## <a name="see-also"></a>另請參閱

[IOleObjectImpl 類別](../../atl/reference/ioleobjectimpl-class.md)<br/>
[ActiveX 控制項介面](/windows/desktop/com/activex-controls-interfaces)<br/>
[類別概觀](../../atl/atl-class-overview.md)
