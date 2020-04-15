---
title: 入入物件巨集
ms.date: 11/04/2016
f1_keywords:
- atlsnap/ATL::BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::BEGIN_SNAPINTOOLBARID_MAP
- atlsnap/ATL::END_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::END_SNAPINTOOLBARID_MAP
- atlsnap/ATL::EXTENSION_SNAPIN_DATACLASS
- atlsnap/ATL::EXTENSION_SNAPIN_NODEINFO_ENTRY
- atlsnap/ATL::SNAPINMENUID
- atlsnap/ATL::SNAPINTOOLBARID_ENTRY
ms.assetid: 4e9850c0-e395-4929-86c9-584a81828053
ms.openlocfilehash: 6a57cdb3c9b6a4448bc954ff754ac9b18fa0b393
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325863"
---
# <a name="snap-in-object-macros"></a>入入物件巨集

這些宏支援卡入擴展。

|||
|-|-|
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|標記捕捉到物件的入網擴展數據類映射的開始。|
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|標記捕捉物件工具列映射的開頭。|
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|標記捕捉到物件的入網擴展數據類映射的末尾。|
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|標記捕捉物件工具列映射的末尾。|
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|為管理單元擴展的數據類創建數據成員。|
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|將入卡擴展數據類輸入到 Snap-in 物件的入網擴展數據類映射中。|
|[斯內普努伊德](#snapinmenuid)|聲明捕捉物件使用的上下文菜單的 ID。|
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|將工具列輸入入卡入物件的工具列映射中。|

## <a name="requirements"></a>需求

**標題:** atlsnap.h

## <a name="begin_extension_snapin_nodeinfo_map"></a><a name="begin_extension_snapin_nodeinfo_map"></a>BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP

標記入卡擴展數據類映射的開頭。

```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```

### <a name="parameters"></a>參數

*類別*<br/>
[在]管理單元擴展數據類的名稱。

### <a name="remarks"></a>備註

使用BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP宏啟動卡入擴展映射,使用[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)宏為每個卡入擴展數據類型添加條目,然後使用[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)宏完成貼圖。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

## <a name="begin_snapintoolbarid_map"></a><a name="begin_snapintoolbarid_map"></a>BEGIN_SNAPINTOOLBARID_MAP

聲明捕捉物件工具列 ID 映射的開頭。

```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```

### <a name="parameters"></a>參數

*_class*<br/>
[在]指定入網物件類。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#106](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]

## <a name="end_extension_snapin_nodeinfo_map"></a><a name="end_extension_snapin_nodeinfo_map"></a>END_EXTENSION_SNAPIN_NODEINFO_MAP

標記卡入擴展數據類映射的末尾。

```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```

### <a name="remarks"></a>備註

使用[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)宏啟動卡入擴展映射,使用[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)宏為每個擴展管理單元數據類型添加條目,然後使用END_EXTENSION_SNAPIN_NODEINFO_MAP宏完成貼圖。

### <a name="example"></a>範例

請參閱[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)的示例。

## <a name="end_snapintoolbarid_map"></a><a name="end_snapintoolbarid_map"></a>END_SNAPINTOOLBARID_MAP

聲明捕捉物件工具列 ID 映射的末尾。

```
END_SNAPINTOOLBARID_MAP( _class )
```

### <a name="parameters"></a>參數

*_class*<br/>
[在]指定入網物件類。

### <a name="example"></a>範例

請參閱[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)的示例。

## <a name="extension_snapin_dataclass"></a><a name="extension_snapin_dataclass"></a>EXTENSION_SNAPIN_DATACLASS

將數據成員添加到**ISnapInItemImpl**派生類的入網擴展數據類。

```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```

### <a name="parameters"></a>參數

*資料類*<br/>
[在]管理單元擴展的數據類。

### <a name="remarks"></a>備註

此類也應輸入到管理單元擴展數據類映射中。 使用[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)宏啟動卡入擴展數據類映射,使用[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)宏為每個卡入擴展數據類型添加條目,以及使用[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)宏完成映射。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

## <a name="extension_snapin_nodeinfo_entry"></a><a name="extension_snapin_nodeinfo_entry"></a>EXTENSION_SNAPIN_NODEINFO_ENTRY

將卡入式擴展數據類添加到卡入擴展數據類映射。

```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```

### <a name="parameters"></a>參數

*資料類*<br/>
[在]管理單元擴展的數據類。

### <a name="remarks"></a>備註

使用[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)宏啟動卡入擴展數據類映射,使用EXTENSION_SNAPIN_NODEINFO_ENTRY宏為每個卡入擴展數據類型添加條目,然後使用[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)宏完成映射。

### <a name="example"></a>範例

請參閱[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)的示例。

## <a name="snapinmenuid"></a><a name="snapinmenuid"></a>斯內普努伊德

使用此宏可以聲明 Snap-In 物件的上下文功能表資源。

```
SNAPINMENUID( id )
```

### <a name="parameters"></a>參數

*id*<br/>
[在]標識入網物件的上下文菜單。

## <a name="snapintoolbarid_entry"></a><a name="snapintoolbarid_entry"></a>SNAPINTOOLBARID_ENTRY

使用此宏在捕捉物件的工具列 ID 映射中輸入工具列 ID。

```
SNAPINTOOLBARID_ENTRY( id )
```

### <a name="parameters"></a>參數

*id*<br/>
[在]標識工具列控件。

### <a name="remarks"></a>備註

BEGIN_SNAPINTOOLBARID_MAP巨集標記工具列 ID 映射的開頭;如果宏[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)宏將標記工具列 ID 映射的開頭。[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)宏標記結束。

### <a name="example"></a>範例

請參閱[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)的示例。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
