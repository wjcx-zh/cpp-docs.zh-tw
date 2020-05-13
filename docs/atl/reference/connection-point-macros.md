---
title: 連接點巨集
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CONNECTION_POINT_MAP
- atlcom/ATL::END_CONNECTION_POINT_MAP
helpviewer_keywords:
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
ms.openlocfilehash: 361cf6ab2c7af142c1d57c002681ccf6e4a87bda
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331489"
---
# <a name="connection-point-macros"></a>連接點巨集

這些宏定義連接點映射和條目。

|||
|-|-|
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|標記連接點映射條目的開頭。|
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|在地圖中輸入連接點。|
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (視覺工作室 2017)類似於CONNECTION_POINT_ENTRY但獲取指向 iid 的指標。|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|標記連接點映射條目的末尾。|

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="begin_connection_point_map"></a><a name="begin_connection_point_map"></a>BEGIN_CONNECTION_POINT_MAP

標記連接點映射條目的開頭。

```
BEGIN_CONNECTION_POINT_MAP(x)
```

### <a name="parameters"></a>參數

*X.*<br/>
[在]包含連接點的類的名稱。

### <a name="remarks"></a>備註

使用BEGIN_CONNECTION_POINT_MAP宏啟動連接點映射,使用[CONNECTION_POINT_ENTRY](#connection_point_entry)宏為每個連接點添加條目,然後使用[END_CONNECTION_POINT_MAP](#end_connection_point_map)宏完成地圖。

有關 ATL 中的連線點的詳細資訊,請參考文章[連接點](../../atl/atl-connection-points.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]

## <a name="connection_point_entry-and-connection_point_entry_p"></a><a name="connection_point_entry"></a>CONNECTION_POINT_ENTRY和CONNECTION_POINT_ENTRY_P

將指定介面的連接點輸入到連接點映射中,以便可以訪問它。

```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```

### <a name="parameters"></a>參數

*Iid*<br/>
[在]要添加到連接點映射的介面的 GUID。

*皮伊德*<br/>
[在]指向要添加的介面的 GUID 的指標。

### <a name="remarks"></a>備註

地圖中的連線點項目由[IConnectionPoint 容器Impl 使用](../../atl/reference/iconnectionpointcontainerimpl-class.md)。 包含連接點映射的類必須從`IConnectionPointContainerImpl`繼承。

使用[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)宏啟動連接點映射,使用CONNECTION_POINT_ENTRY宏為每個連接點添加條目,然後使用[END_CONNECTION_POINT_MAP](#end_connection_point_map)宏完成地圖。

有關 ATL 中的連線點的詳細資訊,請參考文章[連接點](../../atl/atl-connection-points.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]

## <a name="end_connection_point_map"></a><a name="end_connection_point_map"></a>END_CONNECTION_POINT_MAP

標記連接點映射條目的末尾。

```
END_CONNECTION_POINT_MAP()
```

### <a name="remarks"></a>備註

使用[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)宏啟動連接點映射,使用[CONNECTION_POINT_ENTRY](#connection_point_entry)宏為每個連接點添加條目,然後使用END_CONNECTION_POINT_MAP宏完成地圖。

有關 ATL 中的連線點的詳細資訊,請參考文章[連接點](../../atl/atl-connection-points.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)<br/>
[連接點全域函數](../../atl/reference/connection-point-global-functions.md)
