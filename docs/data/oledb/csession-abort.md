---
title: CSession::Abort | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSession.Abort
- CSession::Abort
- ATL.CSession.Abort
- ATL::CSession::Abort
dev_langs:
- C++
helpviewer_keywords:
- Abort method
ms.assetid: 02413b20-c486-451f-b4d7-73a6e8065df8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bfaef7dae1472e8d49bfe70afc99d285e86a8294
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="csessionabort"></a>CSession::Abort
結束交易。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Abort(BOID* pboidReason = NULL,   
   BOOL bRetaining = FALSE,   
   BOOL bAsync = FALSE) const throw();  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[itransaction:: Abort](https://msdn.microsoft.com/en-us/library/ms709833.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CSession 類別](../../data/oledb/csession-class.md)