---
title: 'Cutlprops:: Setpropvalue |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- SetPropValue
- ATL::CUtlProps<T>::SetPropValue
- ATL.CUtlProps<T>.SetPropValue
- ATL.CUtlProps.SetPropValue
- CUtlProps::SetPropValue
- CUtlProps<T>::SetPropValue
- CUtlProps.SetPropValue
- CUtlProps<T>.SetPropValue
- ATL::CUtlProps::SetPropValue
dev_langs:
- C++
helpviewer_keywords:
- SetPropValue method
ms.assetid: 69a703c0-f640-4ca3-8850-0c4e75d52429
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 73f2432a23adf8fe11f759c2caa85d9653040635
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099065"
---
# <a name="cutlpropssetpropvalue"></a>CUtlProps::SetPropValue
在屬性集中設定的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SetPropValue(const GUID* pguidPropSet,  
   DBPROPID dwPropId,  
   VARIANT* pvValue);  
```  
  
#### <a name="parameters"></a>參數  
 `pguidPropSet`  
 [in]PropSet GUID。  
  
 `dwPropId`  
 [in]屬性的索引。  
  
 `pvValue`  
 [in]包含新的屬性值為 variant 的指標。  
  
## <a name="return-value"></a>傳回值  
 `Failure` 失敗和`S_OK`如果成功的話。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [CUtlProps 類別](../../data/oledb/cutlprops-class.md)