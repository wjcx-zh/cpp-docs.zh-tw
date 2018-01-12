---
title: "Irowsetlocateimpl:: Hash |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetLocateImpl::Hash
- IRowsetLocateImpl.Hash
dev_langs: C++
helpviewer_keywords: Hash method
ms.assetid: 7df4386d-80fb-4332-a85f-baae98cdc6e0
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7c3cb64979b8c1ff7a5b9d2e9441a91da0c77f2b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="irowsetlocateimplhash"></a>IRowsetLocateImpl::Hash
傳回雜湊值，指定的書籤。  
  
## <a name="syntax"></a>語法  
  
```  
  
      STDMETHOD ( Hash )(  
   HCHAPTER /* hReserved */,  
   DBBKMARK cbBookmarks,  
   const DBBKMARK* rgcbBookmarks[],  
   const BYTE* rgpBookmarks[],  
   DBHASHVALUE rgHashValues[],  
   DBROWSTATUS rgBookmarkStatus[]   
);  
```  
  
#### <a name="parameters"></a>參數  
 `hReserved`  
 [in]對應至`hChapter`參數[IRowsetLocate::Hash](https://msdn.microsoft.com/en-us/library/ms709697.aspx)。  
  
 其他參數，請參閱[IRowsetLocate::Hash](https://msdn.microsoft.com/en-us/library/ms709697.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [IRowsetLocateImpl 類別](../../data/oledb/irowsetlocateimpl-class.md)