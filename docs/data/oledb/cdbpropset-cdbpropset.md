---
title: "Cdbpropset:: Cdbpropset |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDBPropSet.CDBPropSet
- CDBPropSet::CDBPropSet
- ATL::CDBPropSet::CDBPropSet
- ATL.CDBPropSet.CDBPropSet
dev_langs: C++
helpviewer_keywords: CDBPropSet class, constructor
ms.assetid: 02ae5d9e-c067-47ca-8111-a03e86b5626b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 239f6c0a03186736d35b8d082913aeb76cac1d14
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cdbpropsetcdbpropset"></a>CDBPropSet::CDBPropSet
建構函式。 初始化**Rgpropertysets**， **Rgproperties**，和**guidPropertySet**欄位[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)結構。  
  
## <a name="syntax"></a>語法  
  
```  
  
      CDBPropSet(  
   const GUID& guid   
);  
CDBPropSet(   
   const CDBPropSet& propset    
);  
CDBPropSet( );  
```  
  
#### <a name="parameters"></a>參數  
 `guid`  
 [in]GUID 用來初始化**guidPropertySet**欄位。  
  
 *propset*  
 [in] 複製建構的另一個 `CDBPropSet` 物件。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CDBPropSet 類別](../../data/oledb/cdbpropset-class.md)   
 [Cdbpropset:: Setguid](../../data/oledb/cdbpropset-setguid.md)   
 [DBPROP 結構](https://msdn.microsoft.com/en-us/library/ms717970.aspx)