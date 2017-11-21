---
title: "Irowsetimpl:: Releaserows |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetImpl.ReleaseRows
- ReleaseRows
- IRowsetImpl::ReleaseRows
- ATL::IRowsetImpl::ReleaseRows
- IRowsetImpl.ReleaseRows
dev_langs: C++
helpviewer_keywords: ReleaseRows method
ms.assetid: e4d47be8-8ebf-485b-b1e9-df13e4c8ee8d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 76a4c82a3bc8e739c94ca87754f25037dd53ab0b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetimplreleaserows"></a>IRowsetImpl::ReleaseRows
釋放資料列。  
  
## <a name="syntax"></a>語法  
  
```  
  
      STDMETHOD( ReleaseRows )(  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBROWOPTIONS rgRowOptions[],  
   DBREFCOUNT rgRefCounts[],  
   DBROWSTATUS rgRowStatus[]   
);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[irowset:: Releaserows](https://msdn.microsoft.com/en-us/library/ms719771.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)   
 [Irowsetimpl:: Addrefrows](../../data/oledb/irowsetimpl-addrefrows.md)   
 [IRowsetImpl::RefRows](../../data/oledb/irowsetimpl-refrows.md)