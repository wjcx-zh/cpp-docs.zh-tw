---
title: CFirePropNotifyEvent 類別
ms.date: 11/04/2016
f1_keywords:
- CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnChanged
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnRequestEdit
helpviewer_keywords:
- sinks, notifying of ATL events
- CFirePropNotifyEvent class
- connection points [C++], notifying of events
ms.assetid: eb7a563e-6bce-4cdf-8d20-8c6a5307781b
ms.openlocfilehash: 694127ceccc1d1b55e5da9abca799dff77dcfc60
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417863"
---
# <a name="cfirepropnotifyevent-class"></a>CFirePropNotifyEvent 類別

這個類別會提供方法來通知容器有關控制項屬性變更的接收。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CFirePropNotifyEvent
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|靜止通知容器的接收器，控制項屬性已變更。|
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|靜止通知容器的接收，控制項屬性即將變更。|

## <a name="remarks"></a>備註

`CFirePropNotifyEvent` 有兩個方法，可通知容器的接收，控制項屬性已變更或即將變更。

如果執行控制項的類別衍生自 `IPropertyNotifySink`，當您呼叫 `FireOnRequestEdit` 或 `FireOnChanged`時，就會叫用 `CFirePropNotifyEvent` 方法。 如果您的控制項類別不是衍生自 `IPropertyNotifySink`，這些函式的呼叫會傳回 S_OK。

如需建立控制項的詳細資訊，請參閱[ATL 教學](../../atl/active-template-library-atl-tutorial.md)課程。

## <a name="requirements"></a>需求

**標頭：** atlctl。h

##  <a name="fireonchanged"></a>CFirePropNotifyEvent::FireOnChanged

通知所有已連接的[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)介面（在物件的每個連接點上），指定的物件屬性已變更。

```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>參數

*pUnk*<br/>
在傳送通知之物件 `IUnknown` 的指標。

*dispID*<br/>
在已變更之屬性的識別碼。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

即使您的控制項不支援連接點，也可以安全地呼叫這個函式。

##  <a name="fireonrequestedit"></a>CFirePropNotifyEvent::FireOnRequestEdit

通知所有連接的[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)介面（在物件的每個連接點上），指定的物件屬性即將變更。

```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>參數

*pUnk*<br/>
在傳送通知之物件 `IUnknown` 的指標。

*dispID*<br/>
在要變更之屬性的識別碼。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

即使您的控制項不支援連接點，也可以安全地呼叫這個函式。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)
