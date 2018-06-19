---
title: 'Cbulkrowset:: Movetoratio |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CBulkRowset.MoveToRatio
- ATL::CBulkRowset::MoveToRatio
- MoveToRatio
- CBulkRowset::MoveToRatio
- ATL.CBulkRowset<TAccessor>.MoveToRatio
- ATL::CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset.MoveToRatio
- CBulkRowset<TAccessor>::MoveToRatio
dev_langs:
- C++
helpviewer_keywords:
- MoveToRatio method
ms.assetid: 86be60f5-9341-44c1-8e1e-9174c082d0d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0ab702781ed47a4520b53e9698319b5c245e2dfc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093356"
---
# <a name="cbulkrowsetmovetoratio"></a>CBulkRowset::MoveToRatio
提取資料列從資料列集的小數位置開始。  
  
## <a name="syntax"></a>語法  
  
```
HRESULT MoveToRatio(DBCOUNTITEM nNumerator,  
   DBCOUNTITEM nDenominator)throw();  
```  
  
#### <a name="parameters"></a>參數  
 `nNumerator`  
 [in]用來判斷要從中擷取資料的小數位置分子。  
  
 `nDenominator`  
 [in]用來判斷要從中擷取資料的小數位置分母。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 `MoveToRatio` 擷取資料列大約是根據下列公式：  
  
 `(nNumerator *  RowsetSize ) / nDenominator`  
  
 其中`RowsetSize`是以列數測量的資料列集的大小。 此公式的準確性，取決於特定的提供者。 如需詳細資訊，請參閱[irowsetscroll::](https://msdn.microsoft.com/en-us/library/ms709602.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CBulkRowset 類別](../../data/oledb/cbulkrowset-class.md)