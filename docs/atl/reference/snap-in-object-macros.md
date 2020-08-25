---
title: 嵌入式管理單元物件宏
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
ms.openlocfilehash: 7e006a17ad480ea79f6aeec224278815c8c3f164
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835190"
---
# <a name="snap-in-object-macros"></a>嵌入式管理單元物件宏

這些宏提供嵌入式管理單元擴充功能的支援。

|名稱|描述|
|-|-|
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|標記嵌入式管理單元物件之嵌入式管理單元擴充功能資料類別對應的開頭。|
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|標記嵌入式管理單元物件的工具列地圖開頭。|
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|標記嵌入式管理單元物件之嵌入式管理單元擴充功能資料類別對應的結尾。|
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|標示嵌入式管理單元物件的工具列地圖結尾。|
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|建立嵌入式管理單元延伸模組之資料類別的資料成員。|
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|在嵌入式管理單元物件的嵌入式管理單元擴充功能資料類別對應中，輸入嵌入式管理單元擴充功能資料類別。|
|[SNAPINMENUID](#snapinmenuid)|宣告嵌入式管理單元物件所使用之內容功能表的識別碼。|
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|在嵌入式管理單元物件的工具列地圖中輸入工具列。|

## <a name="requirements"></a>規格需求

**標頭：** atlsnap。h

## <a name="begin_extension_snapin_nodeinfo_map"></a><a name="begin_extension_snapin_nodeinfo_map"></a> BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP

標記嵌入式管理單元擴充功能資料類別對應的開頭。

```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```

### <a name="parameters"></a>參數

*classname*<br/>
在嵌入式管理單元擴充功能資料類別的名稱。

### <a name="remarks"></a>備註

使用 BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP 宏啟動嵌入式管理單元擴充功能對應、使用 [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) 宏新增每個嵌入式管理單元延伸模組資料類型的專案，並使用 [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) 宏完成對應。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

## <a name="begin_snapintoolbarid_map"></a><a name="begin_snapintoolbarid_map"></a> BEGIN_SNAPINTOOLBARID_MAP

宣告嵌入式管理單元物件的工具列識別碼對應開頭。

```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```

### <a name="parameters"></a>參數

*_class*<br/>
在指定嵌入式管理單元物件類別。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#106](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]

## <a name="end_extension_snapin_nodeinfo_map"></a><a name="end_extension_snapin_nodeinfo_map"></a> END_EXTENSION_SNAPIN_NODEINFO_MAP

標記嵌入式管理單元延伸模組資料類別對應的結尾。

```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```

### <a name="remarks"></a>備註

使用 [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) 宏啟動嵌入式管理單元擴充功能對應、使用 [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) 宏為每個延伸模組嵌入式管理單元資料類型新增專案，並使用 END_EXTENSION_SNAPIN_NODEINFO_MAP 宏完成對應。

### <a name="example"></a>範例

請參閱 [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)的範例。

## <a name="end_snapintoolbarid_map"></a><a name="end_snapintoolbarid_map"></a> END_SNAPINTOOLBARID_MAP

宣告嵌入式管理單元物件的工具列識別碼對應結尾。

```
END_SNAPINTOOLBARID_MAP( _class )
```

### <a name="parameters"></a>參數

*_class*<br/>
在指定嵌入式管理單元物件類別。

### <a name="example"></a>範例

請參閱 [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)的範例。

## <a name="extension_snapin_dataclass"></a><a name="extension_snapin_dataclass"></a> EXTENSION_SNAPIN_DATACLASS

將資料成員加入至 **ISnapInItemImpl**衍生類別的嵌入式管理單元擴充功能資料類別。

```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```

### <a name="parameters"></a>參數

*dataClass*<br/>
在嵌入式管理單元擴充功能的資料類別。

### <a name="remarks"></a>備註

此類別也應輸入至嵌入式管理單元擴充功能資料類別對應中。 使用 [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) 宏啟動嵌入式管理單元擴充功能資料類別對應、使用 [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) 宏為每個嵌入式管理單元擴充功能資料類型新增專案，並使用 [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) 宏完成對應。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

## <a name="extension_snapin_nodeinfo_entry"></a><a name="extension_snapin_nodeinfo_entry"></a> EXTENSION_SNAPIN_NODEINFO_ENTRY

將嵌入式管理單元擴充功能資料類別新增至嵌入式管理單元擴充功能資料類別對應。

```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```

### <a name="parameters"></a>參數

*dataClass*<br/>
在嵌入式管理單元擴充功能的資料類別。

### <a name="remarks"></a>備註

使用 [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) 宏啟動嵌入式管理單元擴充功能資料類別對應、使用 EXTENSION_SNAPIN_NODEINFO_ENTRY 宏為每個嵌入式管理單元擴充功能資料類型新增專案，並使用 [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) 宏完成對應。

### <a name="example"></a>範例

請參閱 [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)的範例。

## <a name="snapinmenuid"></a><a name="snapinmenuid"></a> SNAPINMENUID

使用這個宏來宣告嵌入式管理單元物件的內容功能表資源。

```
SNAPINMENUID( id )
```

### <a name="parameters"></a>參數

*id*<br/>
在識別嵌入式管理單元物件的內容功能表。

## <a name="snapintoolbarid_entry"></a><a name="snapintoolbarid_entry"></a> SNAPINTOOLBARID_ENTRY

使用這個宏將工具列識別碼輸入至嵌入式管理單元物件的工具列識別碼對應中。

```
SNAPINTOOLBARID_ENTRY( id )
```

### <a name="parameters"></a>參數

*id*<br/>
在識別工具列控制項。

### <a name="remarks"></a>備註

[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)宏會標示工具列識別碼對應的開頭;[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)宏會標示結尾。

### <a name="example"></a>範例

請參閱 [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)的範例。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
