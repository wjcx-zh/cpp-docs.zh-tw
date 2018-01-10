---
title: "Irowsetupdateimpl:: Undo |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl.Undo
dev_langs: C++
helpviewer_keywords: Undo method
ms.assetid: f3dc7764-050c-4322-9b2f-9ca772a0fb88
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 329a6141ca01678c341ef3890fb0e563a7299915
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="irowsetupdateimplundo"></a>IRowsetUpdateImpl::Undo
復原自上次擷取或更新的資料列的任何變更。  
  
## <a name="syntax"></a>語法  
  
```  
  
      STDMETHOD ( Undo )(  
   HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[ ],  
   DBCOUNTITEM* pcRowsUndone,  
   HROW** prgRowsUndone,  
   DBROWSTATUS** prgRowStatus   
);  
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
  
## <a name="see-also"></a>請參閱  
 [IRowsetUpdateImpl 類別](../../data/oledb/irowsetupdateimpl-class.md)