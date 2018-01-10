---
title: "Csession:: Open |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CSession::Open
- CSession::Open
- CSession.Open
- ATL.CSession.Open
dev_langs: C++
helpviewer_keywords: Open method
ms.assetid: c2050c2c-9817-4857-be49-189f346968f6
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b3aa0f6b694bc594ec00511ce39b7887bf26ecae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="csessionopen"></a>CSession::Open
開啟資料來源物件的新工作階段。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT Open(  
   const CDataSource& ds,  
   DBPROPSET *pPropSet = NULL,  
   ULONG ulPropSets = 0  
) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 `ds`  
 [in]若要開啟工作階段的資料來源。  
  
 *Dbpropset*  
 [in]陣列的指標[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)結構，其中包含要設定屬性和值。 請參閱[屬性集和屬性群組](https://msdn.microsoft.com/en-us/library/ms713696.aspx)中*OLE DB 程式設計人員參考*Windows SDK 中。  
  
 `ulPropSets`  
 [in]數目[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)結構傳入*Dbpropset*引數。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 您必須開啟資料來源物件使用[cdatasource:: Open](../../data/oledb/cdatasource-open.md)再傳遞給`CSession::Open`。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CSession 類別](../../data/oledb/csession-class.md)