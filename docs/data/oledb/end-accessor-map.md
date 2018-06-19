---
title: END_ACCESSOR_MAP |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- END_ACCESSOR_MAP
dev_langs:
- C++
helpviewer_keywords:
- END_ACCESSOR_MAP macro
ms.assetid: ede813c7-46c9-48a6-aa1a-8ebf38e92023
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 647e581a86564221ad409caf9addd03ae3d11fb1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101561"
---
# <a name="endaccessormap"></a>END_ACCESSOR_MAP
存取子對應項目結束標記。  
  
## <a name="syntax"></a>語法  
  
```cpp
END_ACCESSOR_MAP()  
  
```  
  
## <a name="remarks"></a>備註  
 您必須指定資料列集的多重存取子，`BEGIN_ACCESSOR_MAP`並用`BEGIN_ACCESSOR`巨集的每個個別存取子。 `BEGIN_ACCESSOR` 巨集會以 `END_ACCESSOR` 巨集完成。 `BEGIN_ACCESSOR_MAP`巨集已完成，但`END_ACCESSOR_MAP`巨集。  
  
## <a name="example"></a>範例  
 請參閱[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [巨集和全域函式的 OLE DB 消費者樣板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)