---
title: 'Cutlprops:: Getpropvalue |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CUtlProps::GetPropValue
- CUtlProps.GetPropValue
- GetPropValue
dev_langs:
- C++
helpviewer_keywords:
- GetPropValue method
ms.assetid: 9a3fbadb-7814-48f7-96a4-b960fc4ecf2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 00f56c317f9325fa51f7165fc3872b1e4ca6e9da
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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
  
## <a name="see-also"></a>另請參閱  
 [CUtlProps 類別](../../data/oledb/cutlprops-class.md)