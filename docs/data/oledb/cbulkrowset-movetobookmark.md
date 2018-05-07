---
title: 'Cbulkrowset:: Movetobookmark |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CBulkRowset<TAccessor>::MoveToBookmark
- CBulkRowset.MoveToBookmark
- MoveToBookmark
- ATL.CBulkRowset.MoveToBookmark
- CBulkRowset::MoveToBookmark
- ATL::CBulkRowset<TAccessor>::MoveToBookmark
- ATL::CBulkRowset::MoveToBookmark
dev_langs:
- C++
helpviewer_keywords:
- MoveToBookmark method
ms.assetid: 76aab025-819e-4ecd-ae0a-d8d3fb2d2099
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4b1911fe170262e65ef06e65649f837a0b723d05
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cbulkrowsetmovetobookmark"></a>CBulkRowset::MoveToBookmark
擷取書籤所標記的資料列或從該書籤位移至指定位置 (`lSkip`) 的資料列。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark,  
   DBCOUNTITEM lSkip = 0) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `bookmark`  
 [in] 標記您要從中擷取資料之位置的書籤。  
  
 `lSkip`  
 [in] 從書籤到目標資料列的資料列計數。 如果 `lSkip` 為零，將擷取的第一個資料列是已標記書籤的資料列。 如果 `lSkip` 為 1，將擷取的第一個資料列是已標記書籤的資料列之後的資料列。 如果`lSkip`為-1，將擷取的第一個資料列是已標記書籤的資料列之前的資料列。  
  
## <a name="return-value"></a>傳回值  
 請參閱[irowset:: Getdata](https://msdn.microsoft.com/en-us/library/ms716988.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CBulkRowset 類別](../../data/oledb/cbulkrowset-class.md)