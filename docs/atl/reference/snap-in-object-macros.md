---
title: "嵌入式管理單元物件巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4e9850c0-e395-4929-86c9-584a81828053
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 13823feb06e7fecb2e81a01f3c88e3664de01d30
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="snap-in-object-macros"></a>嵌入式管理單元物件巨集
這些巨集提供嵌入式管理單元擴充功能的支援。  
  
|||  
|-|-|  
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|標記的嵌入式管理單元物件的嵌入式管理單元延伸資料類別對應的開頭。|  
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|標記的嵌入式管理單元物件的工具列對應的開頭。|  
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|結束標記的嵌入式管理單元延伸資料類別對應嵌入式管理單元的物件。|  
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|嵌入式管理單元物件工具列對應結束標記。|  
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|建立嵌入式管理單元延伸模組的資料類別資料成員。|  
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|嵌入式管理單元物件的嵌入式管理單元延伸資料類別對應中輸入嵌入式管理單元延伸資料類別。|  
|[SNAPINMENUID](#snapinmenuid)|宣告嵌入式管理單元的物件所使用的內容功能表中的識別碼。|  
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|輸入嵌入式管理單元物件的工具列對應工具列。|  

## <a name="requirements"></a>需求  
 **標頭︰** atlsnap.h 
   
##  <a name="begin_extension_snapin_nodeinfo_map"></a>BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP  
 標記的嵌入式管理單元延伸資料類別對應的開頭。  
  
```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```  
  
### <a name="parameters"></a>參數  
 *類別名稱*  
 [in]嵌入式管理單元延伸資料類別的名稱。  
  
### <a name="remarks"></a>備註  
 啟動您的嵌入式管理單元的延伸模組對應與`BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP`巨集，為您的嵌入式管理單元的延伸模組資料類型與每個新增項目[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)巨集，並完成的對應[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)巨集。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&105;](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]  
  
##  <a name="begin_snapintoolbarid_map"></a>BEGIN_SNAPINTOOLBARID_MAP  
 宣告的嵌入式管理單元物件的工具列識別碼對應的開頭。  
  
```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```  
  
### <a name="parameters"></a>參數  
 `_class`  
 [in]指定的嵌入式管理單元物件類別。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&106;](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]  
  
##  <a name="end_extension_snapin_nodeinfo_map"></a>END_EXTENSION_SNAPIN_NODEINFO_MAP  
 標記嵌入式管理單元延伸資料類別對應的結尾。  
  
```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```  
  
### <a name="remarks"></a>備註  
 啟動您的嵌入式管理單元的延伸模組對應與[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)巨集，為您的延伸嵌入式管理單元資料類型與每個新增項目[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)巨集，並完成的對應`END_EXTENSION_SNAPIN_NODEINFO_MAP`巨集。  
  
### <a name="example"></a>範例  
 請參閱範例[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)。  
  
##  <a name="end_snapintoolbarid_map"></a>END_SNAPINTOOLBARID_MAP  
 宣告對應的結尾工具列 ID 嵌入式管理單元的物件。  
  
```
END_SNAPINTOOLBARID_MAP( _class )
```  
  
### <a name="parameters"></a>參數  
 `_class`  
 [in]指定的嵌入式管理單元物件類別。  
  
### <a name="example"></a>範例  
 請參閱範例[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)。  
  
##  <a name="extension_snapin_dataclass"></a>EXTENSION_SNAPIN_DATACLASS  
 新增嵌入式管理單元延伸資料類別資料成員**ISnapInItemImpl**-衍生的類別。  
  
```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```  
  
### <a name="parameters"></a>參數  
 `dataClass`  
 [in]嵌入式管理單元延伸模組的資料類別。  
  
### <a name="remarks"></a>備註  
 這個類別也應該將輸入嵌入式管理單元延伸資料類別對應。 啟動您的嵌入式管理單元延伸資料類別對應與[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)巨集，為您的嵌入式管理單元的延伸模組資料類型與每個新增項目[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)巨集，並完成的對應[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)巨集。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&105;](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]  
  
##  <a name="extension_snapin_nodeinfo_entry"></a>EXTENSION_SNAPIN_NODEINFO_ENTRY  
 新增嵌入式管理單元延伸資料的類別圖的嵌入式管理單元延伸資料類別。  
  
```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```  
  
### <a name="parameters"></a>參數  
 `dataClass`  
 [in]嵌入式管理單元延伸模組的資料類別。  
  
### <a name="remarks"></a>備註  
 啟動您的嵌入式管理單元延伸資料類別對應與[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)巨集，為您的嵌入式管理單元的延伸模組資料類型與每個新增項目`EXTENSION_SNAPIN_NODEINFO_ENTRY`巨集，並完成的對應[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)巨集。  
  
### <a name="example"></a>範例  
 請參閱範例[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)。  
  
##  <a name="snapinmenuid"></a>SNAPINMENUID  
 您可以使用這個巨集來宣告的嵌入式管理單元物件的內容功能表資源。  
  
```
SNAPINMENUID( id )
```  
  
### <a name="parameters"></a>參數  
 `id`  
 [in]識別的嵌入式管理單元物件的內容功能表。  
  
##  <a name="snapintoolbarid_entry"></a>SNAPINTOOLBARID_ENTRY  
 您可以使用這個巨集輸入嵌入式管理單元物件工具列識別碼對應的工具列 ID。  
  
```
SNAPINTOOLBARID_ENTRY( id )
```  
  
### <a name="parameters"></a>參數  
 `id`  
 [in]識別工具列控制項。  
  
### <a name="remarks"></a>備註  
 [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)巨集標記工具列識別碼對應的開頭; [END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)巨集標記結尾。  
  
### <a name="example"></a>範例  
 請參閱範例[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)。  
  
## <a name="see-also"></a>另請參閱  
 [巨集](../../atl/reference/atl-macros.md)

