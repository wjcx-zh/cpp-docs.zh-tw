---
title: "END_ACCESSOR |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: END_ACCESSOR
dev_langs: C++
helpviewer_keywords: END_ACCESSOR macro
ms.assetid: 26f74167-68c4-4909-a474-73dc7ebc9542
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f0dceb1fe648a67d10fb18b353a5de54fa39caee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="endaccessor"></a>END_ACCESSOR
標記存取子項目的結尾。  
  
## <a name="syntax"></a>語法  
  
```  
  
END_ACCESSOR( )  
  
```  
  
## <a name="remarks"></a>備註  
 您必須指定資料列集的多重存取子，`BEGIN_ACCESSOR_MAP`並用`BEGIN_ACCESSOR`巨集的每個個別存取子。 `BEGIN_ACCESSOR` 巨集會以 `END_ACCESSOR` 巨集完成。 `BEGIN_ACCESSOR_MAP`巨集已完成，但`END_ACCESSOR_MAP`巨集。  
  
## <a name="example"></a>範例  
 請參閱[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [巨集和全域函式的 OLE DB 消費者樣板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)