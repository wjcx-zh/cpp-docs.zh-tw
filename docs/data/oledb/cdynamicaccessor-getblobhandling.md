---
title: 'Cdynamicaccessor:: Getblobhandling |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDynamicAccessor.GetBlobHandling
- CDynamicAccessor::GetBlobHandling
- ATL::CDynamicAccessor::GetBlobHandling
- GetBlobHandling
- CDynamicAccessor.GetBlobHandling
dev_langs:
- C++
helpviewer_keywords:
- GetBlobHandling method
ms.assetid: bbc6dda6-e132-42a3-980d-24e455cbe456
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 51cc3dedb848058257861f901a46e0377115007d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicaccessorgetblobhandling"></a>CDynamicAccessor::GetBlobHandling
擷取 BLOB 處理目前的資料列的值。  
  
## <a name="syntax"></a>語法  
  
```cpp
const DBBLOBHANDLINGENUM GetBlobHandling() const;  
  
```  
  
## <a name="remarks"></a>備註  
 傳回處理值的 BLOB`eBlobHandling`為設定由[SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)