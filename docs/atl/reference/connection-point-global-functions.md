---
title: 連接點全域函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlAdvise
- atlbase/ATL::AtlUnadvise
- atlbase/ATL::AtlAdviseSinkMap
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a1c972be0b4e14d881812195856465dbc7c9e70
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075784"
---
# <a name="connection-point-global-functions"></a>連接點全域函式

這些函式提供的連接點的支援，並接收對應。

> [!IMPORTANT]
>  下表所列出的函數不能在 Windows 執行階段中執行的應用程式。

|||
|-|-|
|[AtlAdvise](#atladvise)|建立物件連接點與用戶端接收器之間的連接。|
|[AtlUnadvise](#atlunadvise)|終止透過所建立的連線`AtlAdvise`。|
|[AtlAdviseSinkMap](#atladvisesinkmap)|建議，或取消通知事件接收對應中的項目。|

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="atladvise"></a>  AtlAdvise

建立物件連接點與用戶端接收器之間的連接。

> [!IMPORTANT]
>  此函式不能在 Windows 執行階段中執行的應用程式。

```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```

### <a name="parameters"></a>參數

*pUnkCP*<br/>
[in]指標`IUnknown`物件的用戶端想要使用連線。

*pUnk*<br/>
[in]指標，用戶端的`IUnknown`。

*iid*<br/>
[in]連接點的 GUID。 一般而言，這是連接點所管理之輸出介面相同。

*pdw*<br/>
[out]指標，可唯一識別連接 cookie。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

接收器會實作連接點所支援之輸出介面。 用戶端會使用*pdw*傳遞至移除連線的 cookie [AtlUnadvise](#atlunadvise)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]

##  <a name="atlunadvise"></a>  AtlUnadvise

終止透過所建立的連線[AtlAdvise](#atladvise)。

> [!IMPORTANT]
>  此函式不能在 Windows 執行階段中執行的應用程式。

```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```

### <a name="parameters"></a>參數

*pUnkCP*<br/>
[in]指標`IUnknown`的用戶端連接使用的物件。

*iid*<br/>
[in]連接點的 GUID。 一般而言，這是連接點所管理之輸出介面相同。

*dw*<br/>
[in]可唯一識別連接 cookie。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]

##  <a name="atladvisesinkmap"></a>  AtlAdviseSinkMap

呼叫此函式可通知或取消通知在物件接收器事件對應中的所有項目。

> [!IMPORTANT]
>  此函式不能在 Windows 執行階段中執行的應用程式。

```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```

### <a name="parameters"></a>參數

*太平洋時間*<br/>
[in]包含接收對應的物件指標。

*bAdvise*<br/>
[in]如果接到; 接收的所有項目，則為 TRUE。如果要 unadvised 接收的所有項目，則為 FALSE。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)<br/>
[連接點巨集](../../atl/reference/connection-point-macros.md)
