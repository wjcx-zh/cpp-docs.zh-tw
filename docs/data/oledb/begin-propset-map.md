---
title: BEGIN_PROPSET_MAP |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- BEGIN_PROPSET_MAP
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_PROPSET_MAP macro
ms.assetid: c3a30618-6025-4d49-8688-a171294d2e93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5b1596797672c0fff92531ff90f67b94bfd6101e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="beginpropsetmap"></a>BEGIN_PROPSET_MAP
標記屬性的開頭設定對應項目。  
  
## <a name="syntax"></a>語法  
  
```cpp
BEGIN_PROPSET_MAP(Class)  
  
```  
  
#### <a name="parameters"></a>參數  
 *類別*  
 [in]指定設定這個屬性的類別。 可以指定下列的 OLE DB 物件屬性集：  
  
-   [資料來源物件](https://msdn.microsoft.com/en-us/library/ms721278.aspx)  
  
-   [工作階段物件](https://msdn.microsoft.com/en-us/library/ms711572.aspx)  
  
-   [命令](https://msdn.microsoft.com/en-us/library/ms724608.aspx)  
  
## <a name="example"></a>範例  
 以下是範例屬性集對應：  
  
 [!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)