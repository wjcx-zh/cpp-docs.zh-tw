---
title: 'Csession:: Open |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CSession::Open
- CSession::Open
- CSession.Open
- ATL.CSession.Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: c2050c2c-9817-4857-be49-189f346968f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cb64e90d780ffde69744b9d9bdc23886f53400b9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098507"
---
# <a name="csessionopen"></a>CSession::Open
開啟資料來源物件的新工作階段。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Open(const CDataSource& ds,  
   DBPROPSET *pPropSet = NULL,  
   ULONG ulPropSets = 0) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `ds`  
 [in]若要開啟工作階段的資料來源。  
  
 *pPropSet*  
 [in]陣列的指標[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)結構，其中包含要設定屬性和值。 請參閱[屬性集和屬性群組](https://msdn.microsoft.com/en-us/library/ms713696.aspx)中*OLE DB 程式設計人員參考*Windows SDK 中。  
  
 `ulPropSets`  
 [in]數目[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)結構傳入*Dbpropset*引數。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 您必須開啟資料來源物件使用[cdatasource:: Open](../../data/oledb/cdatasource-open.md)再傳遞給`CSession::Open`。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CSession 類別](../../data/oledb/csession-class.md)