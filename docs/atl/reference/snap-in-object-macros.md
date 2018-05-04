---
title: 嵌入式管理單元物件巨集 |Microsoft 文件
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
ms.openlocfilehash: ba8a335bbe5424ca04f1db03a3f3ac4bf3cfa9ec
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="snap-in-object-macros"></a>嵌入式管理單元物件巨集
這些巨集嵌入式管理單元擴充功能提供支援。  
  
|||  
|-|-|  
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|標記嵌入式管理單元物件之嵌入式管理單元擴充功能資料類別對應的開頭。|  
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|標記嵌入式管理單元物件工具列對應的開頭。|  
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|結束標記的嵌入式管理單元物件之嵌入式管理單元擴充功能資料類別對應。|  
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|標示工具列對應嵌入式管理單元物件的結尾。|  
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|建立 「 嵌入式管理單元擴充功能的資料類別資料成員。|  
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|輸入嵌入式管理單元物件的嵌入式管理單元擴充功能資料類別對應的嵌入式管理單元延伸資料類別。|  
|[SNAPINMENUID](#snapinmenuid)|宣告的嵌入式管理單元的物件所使用的內容功能表的識別碼。|  
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|輸入嵌入式管理單元物件的工具列對應工具列。|  

## <a name="requirements"></a>需求  
 **標頭：** atlsnap.h 
   
##  <a name="begin_extension_snapin_nodeinfo_map"></a>  BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP  
 標記的嵌入式管理單元擴充功能資料類別對應的開頭。  
  
```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```  
  
### <a name="parameters"></a>參數  
 *classname*  
 [in]嵌入式管理單元延伸資料類別的名稱。  
  
### <a name="remarks"></a>備註  
 開始使用嵌入式管理單元的延伸模組對應`BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP`巨集，新增的嵌入式管理單元擴充功能資料類型，且每個項目[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)巨集，並完成的對應[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)巨集。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]  
  
##  <a name="begin_snapintoolbarid_map"></a>  BEGIN_SNAPINTOOLBARID_MAP  
 宣告的嵌入式管理單元物件的工具列識別碼對應的開頭。  
  
```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```  
  
### <a name="parameters"></a>參數  
 `_class`  
 [in]指定的嵌入式管理單元物件類別。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#106](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]  
  
##  <a name="end_extension_snapin_nodeinfo_map"></a>  END_EXTENSION_SNAPIN_NODEINFO_MAP  
 標示之嵌入式管理單元擴充功能資料類別對應的結尾。  
  
```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```  
  
### <a name="remarks"></a>備註  
 開始使用嵌入式管理單元的延伸模組對應[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)巨集，將項目加入每個您延伸嵌入式管理單元中的資料類型與[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)巨集，完成的對應和`END_EXTENSION_SNAPIN_NODEINFO_MAP`巨集。  
  
### <a name="example"></a>範例  
 請參閱範例的[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)。  
  
##  <a name="end_snapintoolbarid_map"></a>  END_SNAPINTOOLBARID_MAP  
 宣告的結尾工具列識別碼物件的對應嵌入式管理單元。  
  
```
END_SNAPINTOOLBARID_MAP( _class )
```  
  
### <a name="parameters"></a>參數  
 `_class`  
 [in]指定的嵌入式管理單元物件類別。  
  
### <a name="example"></a>範例  
 請參閱範例的[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)。  
  
##  <a name="extension_snapin_dataclass"></a>  EXTENSION_SNAPIN_DATACLASS  
 加入嵌入式管理單元延伸資料類別資料成員**ISnapInItemImpl**-衍生的類別。  
  
```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```  
  
### <a name="parameters"></a>參數  
 `dataClass`  
 [in]嵌入式管理單元擴充功能的資料類別。  
  
### <a name="remarks"></a>備註  
 這個類別也應該將輸入嵌入式管理單元擴充功能資料類別對應。 開始使用嵌入式管理單元擴充功能資料類別對應[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)巨集，新增的嵌入式管理單元擴充功能資料類型，且每個項目[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)巨集，並完成的對應[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)巨集。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]  
  
##  <a name="extension_snapin_nodeinfo_entry"></a>  EXTENSION_SNAPIN_NODEINFO_ENTRY  
 嵌入式管理單元擴充功能資料類別地圖上加嵌入式管理單元擴充功能資料類別。  
  
```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```  
  
### <a name="parameters"></a>參數  
 `dataClass`  
 [in]嵌入式管理單元擴充功能的資料類別。  
  
### <a name="remarks"></a>備註  
 開始使用嵌入式管理單元擴充功能資料類別對應[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)巨集，新增的嵌入式管理單元擴充功能資料類型，且每個項目`EXTENSION_SNAPIN_NODEINFO_ENTRY`巨集，並完成的對應[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)巨集。  
  
### <a name="example"></a>範例  
 請參閱範例的[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)。  
  
##  <a name="snapinmenuid"></a>  SNAPINMENUID  
 您可以使用這個巨集來宣告嵌入式管理單元之物件的內容功能表資源。  
  
```
SNAPINMENUID( id )
```  
  
### <a name="parameters"></a>參數  
 `id`  
 [in]識別的嵌入式管理單元物件的內容功能表。  
  
##  <a name="snapintoolbarid_entry"></a>  SNAPINTOOLBARID_ENTRY  
 若要將工具列識別碼輸入嵌入式管理單元物件工具列 ID 對應中使用這個巨集。  
  
```
SNAPINTOOLBARID_ENTRY( id )
```  
  
### <a name="parameters"></a>參數  
 `id`  
 [in]識別工具列控制項。  
  
### <a name="remarks"></a>備註  
 [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)巨集將標示工具列識別碼對應的開頭; [END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)巨集標記結尾。  
  
### <a name="example"></a>範例  
 請參閱範例的[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)。  
  
## <a name="see-also"></a>另請參閱  
 [巨集](../../atl/reference/atl-macros.md)
