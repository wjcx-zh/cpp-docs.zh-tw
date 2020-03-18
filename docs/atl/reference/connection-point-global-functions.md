---
title: 連接點全域函式
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlAdvise
- atlbase/ATL::AtlUnadvise
- atlbase/ATL::AtlAdviseSinkMap
helpviewer_keywords:
- connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
ms.openlocfilehash: 0313e93ee82bb96f3bfe08e45f70ccfee30dbee6
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417758"
---
# <a name="connection-point-global-functions"></a>連接點全域函式

這些函式會提供連接點和接收對應的支援。

> [!IMPORTANT]
>  下表所列的函數不能用於在 Windows 執行階段中執行的應用程式。

|||
|-|-|
|[AtlAdvise](#atladvise)|建立物件連接點與用戶端接收器之間的連接。|
|[AtlUnadvise](#atlunadvise)|終止透過 `AtlAdvise`建立的連接。|
|[AtlAdviseSinkMap](#atladvisesinkmap)|建議或 unadvises 事件接收器對應中的專案。|

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

##  <a name="atladvise"></a>AtlAdvise

建立物件連接點與用戶端接收器之間的連接。

> [!IMPORTANT]
>  此函式無法在 Windows 執行階段中執行的應用程式中使用。

```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```

### <a name="parameters"></a>參數

*pUnkCP*<br/>
在用戶端想要連接之物件 `IUnknown` 的指標。

*pUnk*<br/>
在用戶端 `IUnknown`的指標。

*iid*<br/>
在連接點的 GUID。 一般來說，這與連接點所管理的傳出介面相同。

*pdw*<br/>
脫銷可唯一識別連接之 cookie 的指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

接收會執行連接點所支援的傳出介面。 用戶端會使用*pdw* cookie 來移除連接，方法是將它傳遞給[AtlUnadvise](#atlunadvise)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]

##  <a name="atlunadvise"></a>AtlUnadvise

終止透過[AtlAdvise](#atladvise)建立的連接。

> [!IMPORTANT]
>  此函式無法在 Windows 執行階段中執行的應用程式中使用。

```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```

### <a name="parameters"></a>參數

*pUnkCP*<br/>
在與用戶端連接之物件 `IUnknown` 的指標。

*iid*<br/>
在連接點的 GUID。 一般來說，這與連接點所管理的傳出介面相同。

*dw*<br/>
在可唯一識別連接的 cookie。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]

##  <a name="atladvisesinkmap"></a>AtlAdviseSinkMap

呼叫此函式可通知或取消通知在物件接收器事件對應中的所有項目。

> [!IMPORTANT]
>  此函式無法在 Windows 執行階段中執行的應用程式中使用。

```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```

### <a name="parameters"></a>參數

*pT*<br/>
在包含接收對應之物件的指標。

*bAdvise*<br/>
在如果要建議所有接收專案，則為 TRUE;如果要 unadvised 所有接收專案，則為 FALSE。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]

## <a name="see-also"></a>另請參閱

[函數](../../atl/reference/atl-functions.md)<br/>
[連接點巨集](../../atl/reference/connection-point-macros.md)
