---
title: "Csimplerow:: Compare |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CSimpleRow.Compare
- CSimpleRow::Compare
dev_langs: C++
helpviewer_keywords: Compare method
ms.assetid: 0bb65f09-c7bc-449b-aa4e-c828cac13510
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 87ee21022aa379820ced0463892be12ee0676d88
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="csimplerowcompare"></a>CSimpleRow::Compare
比較兩個資料列，以查看它們是否參考相同的資料列執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT Compare(   
   CSimpleRow* pRow    
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRow`  
 指標`CSimpleRow`物件。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`值，通常`S_OK`，指出兩個資料列相同的資料列執行個體，或**S_FALSE**，指出兩個資料列不相同。 請參閱[IRowsetIdentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx)中*OLE DB 程式設計人員參考*如需其他可能的傳回值。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [CSimpleRow 類別](../../data/oledb/csimplerow-class.md)   
 [Csimplerow:: Releaserow](../../data/oledb/csimplerow-releaserow.md)   
 [IRowsetImpl::RefRows](../../data/oledb/irowsetimpl-refrows.md)