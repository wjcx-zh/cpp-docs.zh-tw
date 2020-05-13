---
title: IOleControlImpl 類
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
ms.openlocfilehash: 947ec16e91b99cc42cff90abe7df4a5d13576e98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329614"
---
# <a name="iolecontrolimpl-class"></a>IOleControlImpl 類

此類提供介面和實現`IOleControl``IUnknown`的默認實現。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class IOleControlImpl
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`IOleControlImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IOleControlimpl::凍結事件](#freezeevents)|指示容器是否忽略或接受來自控制項的事件。|
|[IOleControlimpl:取得控制資訊](#getcontrolinfo)|填寫有關控制項的鍵盤行為的資訊。 ATL 實現返回E_NOTIMPL。|
|[IOleControlimpl::環境屬性更改](#onambientpropertychange)|通知控制項一個或多個容器的環境屬性已更改。 ATL 實現返回S_OK。|
|[IOleControlimpl::對內記](#onmnemonic)|通知控制使用者已按下指定的擊鍵。 ATL 實現返回E_NOTIMPL。|

## <a name="remarks"></a>備註

類`IOleControlImpl`提供[IOleControl](/windows/win32/api/ocidl/nn-ocidl-iolecontrol)介面的預設實現,並透過`IUnknown`在調試版本中向轉儲設備發送資訊實現。

**相關文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md), 建立[ATL 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IOleControl`

`IOleControlImpl`

## <a name="requirements"></a>需求

**標題:** atlctl.h

## <a name="iolecontrolimplfreezeevents"></a><a name="freezeevents"></a>IOleControlimpl::凍結事件

在 ATL`FreezeEvents`的實現`m_nFreezeEvents``bFreeze`中,如果為 TRUE,則增加控制`m_nFreezeEvents`類`bFreeze`的數據成員, 如果 為 FALSE,則遞減。

```
HRESULT FreezeEvents(BOOL bFreeze);
```

### <a name="remarks"></a>備註

`FreezeEvents`然後返回S_OK。

請參閱[IOleControl:Windows](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-freezeevents) SDK 中的凍結事件。

## <a name="iolecontrolimplgetcontrolinfo"></a><a name="getcontrolinfo"></a>IOleControlimpl:取得控制資訊

填寫有關控制項的鍵盤行為的資訊。

```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```

### <a name="remarks"></a>備註

請參閱[IOleControl:在](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-getcontrolinfo)Windows SDK 中獲取控制資訊。

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

## <a name="iolecontrolimplonambientpropertychange"></a><a name="onambientpropertychange"></a>IOleControlimpl::環境屬性更改

通知控制項一個或多個容器的環境屬性已更改。

```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

請參閱[IOleControl:Windows](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onambientpropertychange) SDK 中的環境屬性更改。

## <a name="iolecontrolimplonmnemonic"></a><a name="onmnemonic"></a>IOleControlimpl::對內記

通知控制使用者已按下指定的擊鍵。

```
HRESULT OnMnemonic(LPMSG pMsg);
```

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱[IOleControl:Windows SDK 中的「OnMnemonic」。](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onmnemonic)

## <a name="see-also"></a>另請參閱

[IOleObjectimpl 類別](../../atl/reference/ioleobjectimpl-class.md)<br/>
[ActiveX 控制介面](/windows/win32/com/activex-controls-interfaces)<br/>
[類別概觀](../../atl/atl-class-overview.md)
