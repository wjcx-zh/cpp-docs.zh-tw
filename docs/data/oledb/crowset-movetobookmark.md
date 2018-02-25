---
title: CRowset::MoveToBookmark | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CRowset::MoveToBookmark
- ATL::CRowset<TAccessor>::MoveToBookmark
- ATL.CRowset.MoveToBookmark
- ATL.CRowset<TAccessor>.MoveToBookmark
- MoveToBookmark
- CRowset::MoveToBookmark
- CRowset.MoveToBookmark
- CRowset<TAccessor>::MoveToBookmark
dev_langs:
- C++
helpviewer_keywords:
- MoveToBookmark method
ms.assetid: 90124723-8daf-4692-ae2f-0db26b5db920
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 81109bf910f24ab2d0cc4d49023537baafdf70c4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="crowsetmovetobookmark"></a>CRowset::MoveToBookmark
擷取書籤所標記的資料列或從該書籤位移至指定位置 (`lSkip`) 的資料列。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark,   
   LONG lSkip = 0) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `bookmark`  
 [in] 標記您要從中擷取資料之位置的書籤。  
  
 `lSkip`  
 [in] 從書籤到目標資料列的資料列計數。 如果 `lSkip` 為零，將擷取的第一個資料列是已標記書籤的資料列。 如果 `lSkip` 為 1，將擷取的第一個資料列是已標記書籤的資料列之後的資料列。 如果`lSkip`為-1，將擷取的第一個資料列是已標記書籤的資料列之前的資料列。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 此方法需要的選擇性介面`IRowsetLocate`，這可能不支援所有提供者; 如果這種情況，方法會傳回**E_NOINTERFACE**。 您也必須設定**DBPROP_IRowsetLocate**至`VARIANT_TRUE`並設定**DBPROP_CANFETCHBACKWARDS**至`VARIANT_TRUE`之前先呼叫**開啟**資料表或命令包含資料列集。  
  
 使用書籤中取用者的相關資訊，請參閱[使用書籤](../../data/oledb/using-bookmarks.md)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)   
 [CRowset::MoveNext](../../data/oledb/crowset-movenext.md)   
 [CRowset::MoveFirst](../../data/oledb/crowset-movefirst.md)   
 [IRowsetLocate::GetRowsAt](https://msdn.microsoft.com/en-us/library/ms723031.aspx)   
 [CRowset::MovePrev](../../data/oledb/crowset-moveprev.md)   
 [CRowset::MoveLast](../../data/oledb/crowset-movelast.md)