---
title: 連接點宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CONNECTION_POINT_MAP
- atlcom/ATL::END_CONNECTION_POINT_MAP
helpviewer_keywords:
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
ms.openlocfilehash: cb8d6f696980ef91d7b43c960dc50289ea8500a6
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417730"
---
# <a name="connection-point-macros"></a>連接點宏

這些宏會定義連接點對應和專案。

|||
|-|-|
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|標記連接點對應專案的開頭。|
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|將連接點輸入對應中。|
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| （Visual Studio 2017）類似于 CONNECTION_POINT_ENTRY，但會取得 iid 的指標。|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|標示連接點對應專案的結尾。|

## <a name="requirements"></a>需求

**標頭：** atlcom.h。h

##  <a name="begin_connection_point_map"></a>BEGIN_CONNECTION_POINT_MAP

標記連接點對應專案的開頭。

```
BEGIN_CONNECTION_POINT_MAP(x)
```

### <a name="parameters"></a>參數

*x*<br/>
在包含連接點的類別名稱。

### <a name="remarks"></a>備註

使用 BEGIN_CONNECTION_POINT_MAP 宏來啟動您的連接點對應、使用[CONNECTION_POINT_ENTRY](#connection_point_entry)宏新增每個連接點的專案，然後使用[END_CONNECTION_POINT_MAP](#end_connection_point_map)宏完成對應。

如需 ATL 中連接點的詳細資訊，請參閱[連接點](../../atl/atl-connection-points.md)一文。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]

##  <a name="connection_point_entry"></a>CONNECTION_POINT_ENTRY 和 CONNECTION_POINT_ENTRY_P

將指定介面的連接點輸入連接點對應，以便存取。

```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```

### <a name="parameters"></a>參數

*iid*<br/>
在要加入至連接點對應之介面的 GUID。

*piid*<br/>
在要 adde 之介面 GUID 的指標。

### <a name="remarks"></a>備註

[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)會使用對應中的連接點專案。 包含連接點對應的類別必須繼承自 `IConnectionPointContainerImpl`。

使用[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)宏來啟動您的連接點對應、使用 CONNECTION_POINT_ENTRY 宏新增每個連接點的專案，然後使用[END_CONNECTION_POINT_MAP](#end_connection_point_map)宏完成對應。

如需 ATL 中連接點的詳細資訊，請參閱[連接點](../../atl/atl-connection-points.md)一文。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]

##  <a name="end_connection_point_map"></a>END_CONNECTION_POINT_MAP

標示連接點對應專案的結尾。

```
END_CONNECTION_POINT_MAP()
```

### <a name="remarks"></a>備註

使用[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)宏來啟動您的連接點對應、使用[CONNECTION_POINT_ENTRY](#connection_point_entry)宏新增每個連接點的專案，然後使用 END_CONNECTION_POINT_MAP 宏完成對應。

如需 ATL 中連接點的詳細資訊，請參閱[連接點](../../atl/atl-connection-points.md)一文。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)<br/>
[連接點全域函式](../../atl/reference/connection-point-global-functions.md)
