---
title: 'Irowsetlocateimpl:: Getrowsbybookmark |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetLocateImpl::GetRowsByBookmark
- IRowsetLocateImpl.GetRowsByBookmark
- GetRowsByBookmark
dev_langs:
- C++
helpviewer_keywords:
- GetRowsByBookmark method
ms.assetid: 07906e42-3582-427e-812a-aa19791e3c56
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 84bfc1333729b9ed097f50ae98fca997b45e7da5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetlocateimplgetrowsbybookmark"></a>IRowsetLocateImpl::GetRowsByBookmark
擷取符合指定的書籤的一或多個資料列。  
  
## <a name="syntax"></a>語法  
  
```cpp
      STDMETHOD (GetRowsByBookmark )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const DBBKMARK rgcbBookmarks[],  
   const BYTE* rgpBookmarks,  
   HROW rghRows[],  
   DBROWSTATUS* rgRowStatus[]);  
```  
  
#### <a name="parameters"></a>參數  
 `hReserved`  
 [in]對應至`hChapter`參數[irowsetlocate:: Getrowsbybookmark](https://msdn.microsoft.com/en-us/library/ms725420.aspx)。  
  
 其他參數，請參閱[irowsetlocate:: Getrowsbybookmark](https://msdn.microsoft.com/en-us/library/ms725420.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="remarks"></a>備註  
 書籤可以是您定義的值或 OLE DB[標準的書籤](https://msdn.microsoft.com/en-us/library/ms712954.aspx)(**DBBMK_FIRST**或**DBBMK_LAST**)。 不會變更游標位置。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [IRowsetLocateImpl 類別](../../data/oledb/irowsetlocateimpl-class.md)   
 [IRowsetLocateImpl::GetRowsAt](../../data/oledb/irowsetlocateimpl-getrowsat.md)