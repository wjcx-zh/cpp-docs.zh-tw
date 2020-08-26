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
ms.openlocfilehash: 1a648f49b0f3715fd322b1099dcebbf194f57a10
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833526"
---
# <a name="connection-point-global-functions"></a>連接點全域函式

這些函式會提供連接點和接收對應的支援。

> [!IMPORTANT]
> 下表所列的函數不能用於在 Windows 執行階段中執行的應用程式。

|函式|描述|
|-|-|
|[AtlAdvise](#atladvise)|建立物件連接點與用戶端接收器之間的連接。|
|[AtlUnadvise](#atlunadvise)|終止透過建立的連接 `AtlAdvise` 。|
|[AtlAdviseSinkMap](#atladvisesinkmap)|建議或 unadvises 事件接收器對應中的專案。|

## <a name="requirements"></a>規格需求

**標頭：** atlbase.h。h

## <a name="atladvise"></a><a name="atladvise"></a> AtlAdvise

建立物件連接點與用戶端接收器之間的連接。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式不能使用這個函數。

```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```

### <a name="parameters"></a>參數

*pUnkCP*<br/>
在 `IUnknown` 用戶端想要連接之物件的指標。

*朋 克*<br/>
在用戶端的指標 `IUnknown` 。

*Iid*<br/>
在連接點的 GUID。 一般來說，這與連接點所管理的輸出介面相同。

*pdw*<br/>
擴展可唯一識別連接之 cookie 的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

接收會實作為連接點所支援的連出介面。 用戶端會使用 *pdw* cookie 來移除連線，方法是將它傳遞至 [AtlUnadvise](#atlunadvise)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]

## <a name="atlunadvise"></a><a name="atlunadvise"></a> AtlUnadvise

終止透過 [AtlAdvise](#atladvise)建立的連接。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式不能使用這個函數。

```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```

### <a name="parameters"></a>參數

*pUnkCP*<br/>
在 `IUnknown` 用戶端所連接之物件的指標。

*Iid*<br/>
在連接點的 GUID。 一般來說，這與連接點所管理的輸出介面相同。

*dw*<br/>
在可唯一識別連接的 cookie。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]

## <a name="atladvisesinkmap"></a><a name="atladvisesinkmap"></a> AtlAdviseSinkMap

呼叫此函式可通知或取消通知在物件接收器事件對應中的所有項目。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式不能使用這個函數。

```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```

### <a name="parameters"></a>參數

*鉑*<br/>
在包含接收對應之物件的指標。

*bAdvise*<br/>
在如果要建議所有接收專案，則為 TRUE;如果要 unadvised 所有接收專案，則為 FALSE。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)<br/>
[連接點宏](../../atl/reference/connection-point-macros.md)
