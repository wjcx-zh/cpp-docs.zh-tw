---
title: 'Cdbpropidset:: Cdbpropidset |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CDBPropIDSet::CDBPropIDSet
- CDBPropIDSet
- CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet::CDBPropIDSet
- ATL.CDBPropIDSet.CDBPropIDSet
dev_langs:
- C++
helpviewer_keywords:
- CDBPropIDSet class, constructor
ms.assetid: e68cc20e-fce2-4cc1-9e9d-05c542334cc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: eb1aa5b832e8be0e90e34c32c9ad76a8c1c314f4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cdbpropidsetcdbpropidset"></a>CDBPropIDSet::CDBPropIDSet
建構函式。 初始化**Rgpropertysets**， **Rgproperties**，以及 （選擇性） **guidPropertySet**欄位[DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx)結構。  
  
## <a name="syntax"></a>語法  
  
```cpp
      CDBPropIDSet(const GUID& guid);  

CDBPropIDSet(const CDBPropIDSet& propidset);  

CDBPropIDSet();  
```  
  
#### <a name="parameters"></a>參數  
 `guid`  
 [in]GUID 用來初始化**guidPropertySet**欄位。  
  
 *propidset*  
 [in] 複製建構的另一個 `CDBPropIDSet` 物件。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDBPropIDSet 類別](../../data/oledb/cdbpropidset-class.md)   
 [CDBPropIDSet::SetGUID](../../data/oledb/cdbpropidset-setguid.md)