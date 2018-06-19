---
title: 'Irowsetupdateimpl:: Getpendingrows |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetUpdateImpl::GetPendingRows
- GetPendingRows
- IRowsetUpdateImpl.GetPendingRows
- ATL::IRowsetUpdateImpl::GetPendingRows
- ATL.IRowsetUpdateImpl.GetPendingRows
dev_langs:
- C++
helpviewer_keywords:
- GetPendingRows method
ms.assetid: 2d1ef748-da6d-4184-98dc-096427358dfd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7728a4275633c7d6ca5c9f8fdb25aa90250105a0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106589"
---
# <a name="irowsetupdateimplgetpendingrows"></a>IRowsetUpdateImpl::GetPendingRows
傳回資料列有暫止的變更的清單。  
  
## <a name="syntax"></a>語法  
  
```cpp
      STDMETHOD (GetPendingRows )(HCHAPTER /* hReserved */,  
   DBPENDINGSTATUS dwRowStatus,  
   DBCOUNTITEM* pcPendingRows,  
   HROW** prgPendingRows,  
   DBPENDINGSTATUS** prgPendingStatus);  
```  
  
#### <a name="parameters"></a>參數  
 `hReserved`  
 [in]對應至`hChapter`中的參數[IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/en-us/library/ms719626.aspx)。  
  
 其他參數，請參閱[IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/en-us/library/ms719626.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/en-us/library/ms719626.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [IRowsetUpdateImpl 類別](../../data/oledb/irowsetupdateimpl-class.md)