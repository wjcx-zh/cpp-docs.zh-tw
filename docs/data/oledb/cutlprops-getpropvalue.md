---
title: CUtlProps::GetPropValue | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CUtlProps::GetPropValue
- CUtlProps.GetPropValue
- GetPropValue
dev_langs:
- C++
helpviewer_keywords:
- GetPropValue method
ms.assetid: 9a3fbadb-7814-48f7-96a4-b960fc4ecf2e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c4e9ea040c9ec458f100beb4c9cd2516ac167052
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="cutlpropsgetpropvalue"></a>CUtlProps::GetPropValue
從屬性集合取得的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp
      OUT_OF_LINE HRESULT GetPropValue(const GUID* pguidPropSet,  
   DBPROPID dwPropId,  
   VARIANT* pvValue);  
```  
  
#### <a name="parameters"></a>參數  
 `pguidPropSet`  
 [in]PropSet GUID。  
  
 `dwPropId`  
 [in]屬性的索引。  
  
 `pvValue`  
 [out]包含新的屬性值為 variant 的指標。  
  
## <a name="return-value"></a>傳回值  
 `Failure` 失敗和`S_OK`如果成功的話。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [CUtlProps 類別](../../data/oledb/cutlprops-class.md)