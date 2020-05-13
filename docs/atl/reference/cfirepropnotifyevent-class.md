---
title: CFireProp 通知事件類別
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
ms.openlocfilehash: 1dfce42176341d74ffc7d9b42f856e71b17bf4f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326961"
---
# <a name="cfirepropnotifyevent-class"></a>CFireProp 通知事件類別

此類提供了有關控制項屬性更改的通知容器接收器的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CFirePropNotifyEvent
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFireProp通知事件::火種](#fireonchanged)|(靜態)通知容器的接收器控制件屬性已更改。|
|[CFireProp通知事件::火對請求編輯](#fireonrequestedit)|(靜態)通知容器的接收器控制件屬性即將更改。|

## <a name="remarks"></a>備註

`CFirePropNotifyEvent`有兩種方法通知容器的接收器控制項屬性已更改或即將更改。

如果實現控制項的`IPropertyNotifySink`類派生自調`CFirePropNotifyEvent``FireOnRequestEdit`用`FireOnChanged`或時調用的方法。 如果控件類不是派生自`IPropertyNotifySink`,則對這些函數的調用將返回S_OK。

有關建立控制項的詳細資訊,請參閱[ATL 教程](../../atl/active-template-library-atl-tutorial.md)。

## <a name="requirements"></a>需求

**標題:** atlctl.h

## <a name="cfirepropnotifyeventfireonchanged"></a><a name="fireonchanged"></a>CFireProp通知事件::火種

通知所有連接的[IProperty Notify Sink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)介面(在物件的每個連接點上),指定物件屬性已更改。

```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>參數

*龐克*<br/>
[在]指向`IUnknown`發送通知的物件的指標。

*脫從ID*<br/>
[在]已更改的屬性的標識碼。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

即使控件不支援連接點,此函數也是安全的調用。

## <a name="cfirepropnotifyeventfireonrequestedit"></a><a name="fireonrequestedit"></a>CFireProp通知事件::火對請求編輯

通知所有連接的[IProperty Notify Sink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)介面(在物件的每個連接點上),指定物件屬性即將更改。

```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>參數

*龐克*<br/>
[在]指向`IUnknown`發送通知的物件的指標。

*脫從ID*<br/>
[在]要更改的屬性的標識碼。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

即使控件不支援連接點,此函數也是安全的調用。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
