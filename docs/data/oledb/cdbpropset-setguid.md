---
title: CDBPropSet::SetGUID | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CDBPropSet.SetGUID
- CDBPropSet.SetGUID
- ATL::CDBPropSet::SetGUID
- SetGUID
- CDBPropSet::SetGUID
dev_langs:
- C++
helpviewer_keywords:
- SetGUID method
- AddProperty method
ms.assetid: a4cce036-cf1f-4897-9712-7b01eaf887ff
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: edf9720e0f116060a06ffa56bf5c3e6c4c8691e1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="cdbpropsetsetguid"></a>CDBPropSet::SetGUID
設定**guidPropertySet**欄位**DBPROPSET**結構。  
  
## <a name="syntax"></a>語法  
  
```cpp
      void SetGUID(const GUID& guid) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `guid`  
 [in]若要設定使用 GUID **guidPropertySet**欄位[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)結構。  
  
## <a name="remarks"></a>備註  
 這個欄位可以設定[建構函式](../../data/oledb/cdbpropset-cdbpropset.md)以及。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CDBPropSet 類別](../../data/oledb/cdbpropset-class.md)