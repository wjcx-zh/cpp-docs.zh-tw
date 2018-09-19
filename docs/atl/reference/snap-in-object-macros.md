---
title: 嵌入式管理單元物件巨集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlsnap/ATL::BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::BEGIN_SNAPINTOOLBARID_MAP
- atlsnap/ATL::END_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::END_SNAPINTOOLBARID_MAP
- atlsnap/ATL::EXTENSION_SNAPIN_DATACLASS
- atlsnap/ATL::EXTENSION_SNAPIN_NODEINFO_ENTRY
- atlsnap/ATL::SNAPINMENUID
- atlsnap/ATL::SNAPINTOOLBARID_ENTRY
dev_langs:
- C++
ms.assetid: 4e9850c0-e395-4929-86c9-584a81828053
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d37c8c9d319495c3247bf98d9ed3c8f58063ae56
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050550"
---
# <a name="snap-in-object-macros"></a>嵌入式管理單元物件巨集

這些巨集提供嵌入式管理單元延伸模組的支援。

|||
|-|-|
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|標記物件嵌入式管理單元中的嵌入式管理單元延伸模組資料類別對應的開頭。|
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|標記工具列物件的對應嵌入式管理單元的開頭。|
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|結束標記的物件 嵌入式管理單元中的嵌入式管理單元延伸模組資料類別對應。|
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|結束標記的工具列物件的對應嵌入式管理單元。|
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|建立嵌入式管理單元延伸模組的資料類別的資料成員。|
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|輸入嵌入式管理單元物件的嵌入式管理單元延伸模組資料類別對應中的嵌入式管理單元延伸模組資料類別。|
|[SNAPINMENUID](#snapinmenuid)|宣告嵌入式管理單元物件所使用的內容功能表的識別碼。|
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|輸入嵌入式管理單元物件的工具列對應 工具列。|  

## <a name="requirements"></a>需求

**標頭：** atlsnap.h

##  <a name="begin_extension_snapin_nodeinfo_map"></a>  BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP

標示嵌入式管理單元延伸模組資料類別對應表的開頭。

```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```

### <a name="parameters"></a>參數

*classname*<br/>
[in]嵌入式管理單元延伸模組資料類別的名稱。

### <a name="remarks"></a>備註

啟動您的嵌入式管理單元延伸模組對應 BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP 巨集、 新增的每個與您嵌入式管理單元延伸模組資料類型的項目[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)巨集，並完成地圖[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)巨集。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

##  <a name="begin_snapintoolbarid_map"></a>  BEGIN_SNAPINTOOLBARID_MAP

宣告對應的開頭工具列 ID 嵌入式管理單元的物件。

```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```

### <a name="parameters"></a>參數

*（_c)*<br/>
[in]指定的嵌入式管理單元物件類別。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#106](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]

##  <a name="end_extension_snapin_nodeinfo_map"></a>  END_EXTENSION_SNAPIN_NODEINFO_MAP

將標記嵌入式管理單元延伸模組資料類別 map 的結尾。

```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```

### <a name="remarks"></a>備註

開始使用您嵌入式管理單元延伸模組的對應[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)巨集，新增的每個與您延伸模組 嵌入式管理單元中的資料類型的項目[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)巨集，並完成 END_EXTENSION_SNAPIN_NODEINFO_MAP 巨集對應。

### <a name="example"></a>範例

範例，請參閱[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)。

##  <a name="end_snapintoolbarid_map"></a>  END_SNAPINTOOLBARID_MAP

宣告嵌入式管理單元物件工具列 ID map 的結尾。

```
END_SNAPINTOOLBARID_MAP( _class )
```

### <a name="parameters"></a>參數

*（_c)*<br/>
[in]指定的嵌入式管理單元物件類別。

### <a name="example"></a>範例

範例，請參閱[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)。

##  <a name="extension_snapin_dataclass"></a>  EXTENSION_SNAPIN_DATACLASS

將資料成員新增至嵌入式管理單元延伸模組的資料類別，如**ISnapInItemImpl**-衍生的類別。

```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```

### <a name="parameters"></a>參數

*dataClass*<br/>
[in]嵌入式管理單元延伸模組的資料類別。

### <a name="remarks"></a>備註

這個類別也應該輸入嵌入式管理單元延伸模組資料類別對應表中。 開始使用嵌入式管理單元延伸模組資料類別對應[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)巨集，您使用的嵌入式管理單元延伸模組資料類型的每個新增項目[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)巨集，並完成地圖[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)巨集。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

##  <a name="extension_snapin_nodeinfo_entry"></a>  EXTENSION_SNAPIN_NODEINFO_ENTRY

新增嵌入式管理單元延伸模組資料類別圖的嵌入式管理單元延伸模組資料類別。

```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```

### <a name="parameters"></a>參數

*dataClass*<br/>
[in]嵌入式管理單元延伸模組的資料類別。

### <a name="remarks"></a>備註

開始使用嵌入式管理單元延伸模組資料類別對應[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)巨集，新增的每個 EXTENSION_SNAPIN_NODEINFO_ENTRY 巨集，您嵌入式管理單元延伸模組資料類型的項目，以及完成對應具有[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)巨集。

### <a name="example"></a>範例

範例，請參閱[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)。

##  <a name="snapinmenuid"></a>  SNAPINMENUID

您可以使用這個巨集來宣告的嵌入式管理單元物件的內容功能表資源。

```
SNAPINMENUID( id )
```

### <a name="parameters"></a>參數

*id*<br/>
[in]識別的嵌入式管理單元物件的內容功能表。

##  <a name="snapintoolbarid_entry"></a>  SNAPINTOOLBARID_ENTRY

您可以使用這個巨集，工具列 ID 輸入嵌入式管理單元物件工具列識別碼的對應。

```
SNAPINTOOLBARID_ENTRY( id )
```

### <a name="parameters"></a>參數

*id*<br/>
[in]識別工具列控制項。

### <a name="remarks"></a>備註

[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)巨集標記工具列識別碼對應的開頭，而[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)巨集標記結尾。

### <a name="example"></a>範例

範例，請參閱[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
