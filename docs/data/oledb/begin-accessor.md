---
title: BEGIN_ACCESSOR |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- BEGIN_ACCESSOR
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_ACCESSOR macro, syntax
- BEGIN_ACCESSOR macro
ms.assetid: 59d0ff3e-7cfd-4ce8-9a1c-d664c0892a52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0ffb1d506a198586a5a625664f21c29954aada40
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089841"
---
# <a name="beginaccessor"></a>BEGIN_ACCESSOR
標記存取子項目的開頭。  
  
## <a name="syntax"></a>語法  
  
```  
BEGIN_ACCESSOR(num, bAuto)  
```  
  
#### <a name="parameters"></a>參數  
 *num*  
 [in]在此存取子對應中存取子的零位移數。  
  
 *bAuto*  
 [in]指定此存取子是可自動存取子，還是手動存取子。 如果**true**，存取子是自動; 如果**false**，存取子是手動。 自動存取子會表示為您擷取資料移動作業。  
  
## <a name="remarks"></a>備註  
 如果資料列集上的多個存取子，您必須指定`BEGIN_ACCESSOR_MAP`並用`BEGIN_ACCESSOR`巨集的每個個別存取子。 `BEGIN_ACCESSOR` 巨集會以 `END_ACCESSOR` 巨集完成。 `BEGIN_ACCESSOR_MAP`巨集已完成，但`END_ACCESSOR_MAP`巨集。  
  
## <a name="example"></a>範例  
 請參閱[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [巨集和全域函式的 OLE DB 消費者樣板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [END_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)