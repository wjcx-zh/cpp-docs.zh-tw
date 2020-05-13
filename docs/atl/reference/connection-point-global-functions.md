---
title: 連接點全域函數
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlAdvise
- atlbase/ATL::AtlUnadvise
- atlbase/ATL::AtlAdviseSinkMap
helpviewer_keywords:
- connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
ms.openlocfilehash: 6474297f8b9adf04541f7d232fb88d5e52d4e88c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331523"
---
# <a name="connection-point-global-functions"></a>連接點全域函數

這些功能支援連接點和接收器貼圖。

> [!IMPORTANT]
> 下表中列出的函數不能在 Windows 執行時中執行的應用程式中使用。

|||
|-|-|
|[AtlAdvise](#atladvise)|建立物件連接點與用戶端接收器之間的連接。|
|[AtlUnadvise](#atlunadvise)|終止通過`AtlAdvise`建立的連接。|
|[AtlAdviseSinkMap](#atladvisesinkmap)|建議或不建議事件接收器地圖中的條目。|

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="atladvise"></a><a name="atladvise"></a>Atl建議

建立物件連接點與用戶端接收器之間的連接。

> [!IMPORTANT]
> 此函數不能在 Windows 運行時中執行的應用程式中使用。

```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```

### <a name="parameters"></a>參數

*pUnkCP*<br/>
[在]指向用戶端要連接`IUnknown`的物件的指標。

*龐克*<br/>
[在]指向用戶端的`IUnknown`指標。

*Iid*<br/>
[在]連接點的 GUID。 通常,這與連接點管理的傳出介面相同。

*pdw*<br/>
[出]指向唯一標識連接的 Cookie 的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

接收器實現連接點支援的傳出介面。 用戶端使用*pdw* Cookie 將其傳遞給[AtlUn 建議](#atlunadvise)來刪除連接。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]

## <a name="atlunadvise"></a><a name="atlunadvise"></a>AtlUn建議

終止通過[AtlAdvise](#atladvise)建立的連接。

> [!IMPORTANT]
> 此函數不能在 Windows 運行時中執行的應用程式中使用。

```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```

### <a name="parameters"></a>參數

*pUnkCP*<br/>
[在]指向用戶端所連接`IUnknown`的物件的指標。

*Iid*<br/>
[在]連接點的 GUID。 通常,這與連接點管理的傳出介面相同。

*dw*<br/>
[在]唯一標識連接的 Cookie。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]

## <a name="atladvisesinkmap"></a><a name="atladvisesinkmap"></a>AtlAdviseSinkMap

呼叫此函式可通知或取消通知在物件接收器事件對應中的所有項目。

> [!IMPORTANT]
> 此函數不能在 Windows 運行時中執行的應用程式中使用。

```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```

### <a name="parameters"></a>參數

*鉑*<br/>
[在]指向包含接收器貼圖的對象的指標。

*b 建議*<br/>
[在]如果建議所有接收器條目,則為 TRUE;如果所有接收器條目均未通知,則 FALSE。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)<br/>
[連接點巨集](../../atl/reference/connection-point-macros.md)
