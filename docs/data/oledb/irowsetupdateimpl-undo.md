---
title: 'Irowsetupdateimpl:: Undo |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl.Undo
dev_langs:
- C++
helpviewer_keywords:
- Undo method
ms.assetid: f3dc7764-050c-4322-9b2f-9ca772a0fb88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d98465d396084c157c40bdca41c3daac46bc4ad7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetupdateimplundo"></a>IRowsetUpdateImpl::Undo
復原自上次擷取或更新的資料列的任何變更。  
  
## <a name="syntax"></a>語法  
  
```cpp
      STDMETHOD (Undo )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[ ],  
   DBCOUNTITEM* pcRowsUndone,  
   HROW** prgRowsUndone,  
   DBROWSTATUS** prgRowStatus);  
```  
  
#### <a name="parameters"></a>參數  
 `hReserved`  
 [in]對應至`hChapter`中的參數[IRowsetUpdate::Undo](https://msdn.microsoft.com/en-us/library/ms719655.aspx)。  
  
 *pcRowsUndone*  
 [out]對應至`pcRows`中的參數[IRowsetUpdate::Undo](https://msdn.microsoft.com/en-us/library/ms719655.aspx)。  
  
 *prgRowsUndone*  
 [in]對應至*prgRows*中的參數[IRowsetUpdate::Undo](https://msdn.microsoft.com/en-us/library/ms719655.aspx)。  
  
 其他參數，請參閱[IRowsetUpdate::Undo](https://msdn.microsoft.com/en-us/library/ms719655.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [IRowsetUpdateImpl 類別](../../data/oledb/irowsetupdateimpl-class.md)