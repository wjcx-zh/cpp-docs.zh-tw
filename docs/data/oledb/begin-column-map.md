---
title: "BEGIN_COLUMN_MAP |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BEGIN_COLUMN_MAP
dev_langs: C++
helpviewer_keywords: BEGIN_COLUMN_MAP macro
ms.assetid: d6ffe633-e0da-4e33-8faa-f7f259d05420
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 29e62e08ef03d863b17ea0d269cf049b23602774
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="begincolumnmap"></a>BEGIN_COLUMN_MAP
標記資料行對應項目的開頭。  
  
## <a name="syntax"></a>語法  
  
```  
  
BEGIN_COLUMN_MAP(  
x  
 )  
  
```  
  
#### <a name="parameters"></a>參數  
 *x*  
 [in] 衍生自 `CAccessor`之使用者資料錄類別的名稱。  
  
## <a name="remarks"></a>備註  
 如果資料列集上只有單一存取子，就會使用此巨集。 如果資料列集上有多個存取子，請使用 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。  
  
 `BEGIN_COLUMN_MAP` 巨集會以 `END_COLUMN_MAP` 巨集完成。 當使用者資料錄中只需要一個存取子時，就會使用此巨集。  
  
 資料行會對應至您想要繫結之資料列集中的欄位。  
  
## <a name="example"></a>範例  
 以下是範例資料行和參數對應︰  
  
 <!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [巨集和全域函式的 OLE DB 消費者樣板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [COLUMN_ENTRY_EX](../../data/oledb/column-entry-ex.md)